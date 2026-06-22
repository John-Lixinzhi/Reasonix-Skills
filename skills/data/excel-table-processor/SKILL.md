---
name: excel-table-processor
description: [data] Excel table processor - USE when processing Excel spreadsheets/student data. DO preserve format, normalize names, sort, renumber. NOT for simple CSV. Triggers: excel/table/spreadsheet/student/attendance
---

# Excel 统计表处理 Skill

## 适用场景
处理学生返校/请假等统计 Excel 表格，需要：
- 保留原始格式（合并单元格、列宽、行高、字体、对齐、汇总行）
- 修改数据内容（班级标准化、排序、统一学院、重新编号）
- 按日期筛选（如保留22号以后的记录）

## 核心原则
**不要用 `xlsx`（SheetJS）的 `aoa_to_sheet` 重新建表**，那会丢失所有格式。
**必须用 `exceljs` 原地修改单元格的 `.value`**，样式完全不动。

## 步骤

### 1. 安装依赖
```bash
cd /d <桌面路径> && npm install exceljs
```

### 2. 脚本核心结构

```javascript
const ExcelJS = require('exceljs');
const path = require('path');
const fs = require('fs');

const DESKTOP = 'C:\\Users\\john\\Desktop';

async function process(inputFile, outputFile, options = {}) {
  const wb = new ExcelJS.Workbook();
  await wb.xlsx.readFile(inputFile);
  const ws = wb.getWorksheet(1);
  const totalRows = ws.rowCount;

  // ========== A. 读取所有单元格到内存 ==========
  const mem = {};
  for (let r = 1; r <= totalRows; r++) {
    const row = ws.getRow(r);
    mem[r] = [];
    for (let c = 1; c <= 8; c++) {
      const cell = row.getCell(c);
      mem[r][c] = {
        value: cell.value,
        style: JSON.parse(JSON.stringify(cell.style || {})),
      };
    }
  }

  // ========== B. 识别行类型 ==========
  // Row 1: 标题, Row 2: 表头
  // 数据行: D列(4)有值且不是汇总行
  // 汇总行: D列包含"学院总人数"/"实到人数"/"未到人数"
  const dataRows = [], tailRows = [];
  for (let r = 3; r <= totalRows; r++) {
    const v = mem[r]?.[4]?.value;
    if (v && typeof v === 'string') {
      if (/学院总人数|实到人数|未到人数/.test(v)) tailRows.push(r);
      else dataRows.push(r);
    } else {
      tailRows.push(r);
    }
  }

  function gv(r, c) { return mem[r]?.[c]?.value ?? ''; }

  // ========== C. 提取并处理数据 ==========
  let records = dataRows.map(r => ({
    rowNum: r,
    cls: String(gv(r, 3) || ''),
    name: String(gv(r, 4) || ''),
    returnTime: gv(r, 8),
  }));

  // 班级标准化
  records.forEach(r => {
    r.cls = r.cls
      .replace(/^信息工程/, '信息')
      .replace(/^电子信息工程/, '电信')
      .replace(/^通信工程/, '通信')
      .replace(/^集成电路/, '集电');
  });

  // 排序（按拼音）
  records.sort((a, b) => {
    const ma = a.cls.match(/^([^\d]+)(\d+)$/);
    const mb = b.cls.match(/^([^\d]+)(\d+)$/);
    if (ma && mb) {
      const cmp = ma[1].localeCompare(mb[1], 'zh-CN');
      return cmp !== 0 ? cmp : parseInt(ma[2],10) - parseInt(mb[2],10);
    }
    return a.cls.localeCompare(b.cls, 'zh-CN');
  });

  // ========== D. 写回数据（只改value，style不动） ==========
  for (let i = 0; i < records.length; i++) {
    const row = ws.getRow(dataRows[i]);
    row.getCell(1).value = i + 1;  // 重新编号
    row.getCell(2).value = '通信与人工智能学院、集成电路学院';  // 统一学院
    row.getCell(3).value = records[i].cls;
    row.getCell(4).value = String(records[i].name).trim();
    row.getCell(5).value = String(gv(records[i].rowNum, 5) || '').trim();
    row.getCell(6).value = String(gv(records[i].rowNum, 6) || '').trim();
    row.getCell(7).value = String(gv(records[i].rowNum, 7) || '').trim();
    row.getCell(8).value = String(gv(records[i].rowNum, 8) || '').trim();
    row.commit();
  }

  await wb.xlsx.writeFile(outputFile);
}

// ========== 筛选版（22号+） ==========
// 同上 + 删除中间行 + 修正合并
async function processFiltered(inputFile, outputFile) {
  const wb = new ExcelJS.Workbook();
  await wb.xlsx.readFile(inputFile);
  const ws = wb.getWorksheet(1);
  const merges = ws.model.merges ? [...ws.model.merges] : [];

  // ... 同样读内存、识别行、提取数据、标准化、排序 ...

  // 筛选：保留22号+，排除21号
  function isDate21(t) {
    if (!t) return false;
    const s = String(t).trim();
    return /21[号日]/.test(s) || /21[晚早中下夜点时分]/.test(s);
  }
  const keep = records.filter(r => {
    const t = r.returnTime;
    if (!t || String(t).trim() === '') return true;
    if (isDate21(t)) return false;
    return true;
  });

  // 写数据到前 N 行
  // 删除中间多余行（从下往上）
  const firstDel = dataRows[0] + keep.length;
  const lastDel = tailRows[0] - 1;
  if (firstDel <= lastDel) {
    for (let r = lastDel; r >= firstDel; r--) ws.spliceRows(r, 1);
  }

  // 修正合并单元格（汇总行合并调整到新行号）
  if (merges.length > 0) {
    const newLastRow = ws.rowCount;
    const newMerges = [];
    for (const m of merges) {
      const ms = typeof m === 'string' ? m : '';
      const parts = ms.match(/^([A-Z]+)(\d+):([A-Z]+)(\d+)$/);
      if (parts) {
        const r2 = parseInt(parts[4], 10);
        if (r2 > dataRows[dataRows.length-1]) {
          // 尾部合并调整到新最后一行
          newMerges.push({ start: { row: newLastRow, col: 1 }, end: { row: newLastRow, col: 8 } });
        } else {
          newMerges.push(m);
        }
      } else { newMerges.push(m); }
    }
    ws.model.merges = newMerges;
  }

  await wb.xlsx.writeFile(outputFile);
}
```

## 关键要点
1. **永远用 `exceljs`**，不要用 `xlsx`（SheetJS）的 `aoa_to_sheet`
2. **只改 `.value`**，不改 `.style`，样式自然保留
3. 先读所有数据到内存再处理，避免读写交叉
4. `spliceRows` 删除行时**从下往上**删，避免行号变化
5. 删除行后要**手动修正合并单元格**的引用
6. 汇总行如果被清空了值要补回 A 列，并重新 merged
7. 班级标准化规则按需调整：信息工程→信息、电子信息工程→电信、通信工程→通信、集成电路→集电
