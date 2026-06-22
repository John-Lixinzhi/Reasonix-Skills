---
name: excel-table-processor
description: [data] Excel table processor - USE when processing Excel spreadsheets/student data. DO preserve format, normalize names, sort, renumber. NOT for simple CSV. Triggers: excel/table/spreadsheet/student/attendance
---

# Excel 缁熻琛ㄥ鐞?Skill

## 閫傜敤鍦烘櫙
澶勭悊瀛︾敓杩旀牎/璇峰亣绛夌粺璁?Excel 琛ㄦ牸锛岄渶瑕侊細
- 淇濈暀鍘熷鏍煎紡锛堝悎骞跺崟鍏冩牸銆佸垪瀹姐€佽楂樸€佸瓧浣撱€佸榻愩€佹眹鎬昏锛?- 淇敼鏁版嵁鍐呭锛堢彮绾ф爣鍑嗗寲銆佹帓搴忋€佺粺涓€瀛﹂櫌銆侀噸鏂扮紪鍙凤級
- 鎸夋棩鏈熺瓫閫夛紙濡備繚鐣?2鍙蜂互鍚庣殑璁板綍锛?
## 鏍稿績鍘熷垯
**涓嶈鐢?`xlsx`锛圫heetJS锛夌殑 `aoa_to_sheet` 閲嶆柊寤鸿〃**锛岄偅浼氫涪澶辨墍鏈夋牸寮忋€?**蹇呴』鐢?`exceljs` 鍘熷湴淇敼鍗曞厓鏍肩殑 `.value`**锛屾牱寮忓畬鍏ㄤ笉鍔ㄣ€?
## 姝ラ

### 1. 瀹夎渚濊禆
```bash
cd /d <妗岄潰璺緞> && npm install exceljs
```

### 2. 鑴氭湰鏍稿績缁撴瀯

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

  // ========== A. 璇诲彇鎵€鏈夊崟鍏冩牸鍒板唴瀛?==========
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

  // ========== B. 璇嗗埆琛岀被鍨?==========
  // Row 1: 鏍囬, Row 2: 琛ㄥご
  // 鏁版嵁琛? D鍒?4)鏈夊€间笖涓嶆槸姹囨€昏
  // 姹囨€昏: D鍒楀寘鍚?瀛﹂櫌鎬讳汉鏁?/"瀹炲埌浜烘暟"/"鏈埌浜烘暟"
  const dataRows = [], tailRows = [];
  for (let r = 3; r <= totalRows; r++) {
    const v = mem[r]?.[4]?.value;
    if (v && typeof v === 'string') {
      if (/瀛﹂櫌鎬讳汉鏁皘瀹炲埌浜烘暟|鏈埌浜烘暟/.test(v)) tailRows.push(r);
      else dataRows.push(r);
    } else {
      tailRows.push(r);
    }
  }

  function gv(r, c) { return mem[r]?.[c]?.value ?? ''; }

  // ========== C. 鎻愬彇骞跺鐞嗘暟鎹?==========
  let records = dataRows.map(r => ({
    rowNum: r,
    cls: String(gv(r, 3) || ''),
    name: String(gv(r, 4) || ''),
    returnTime: gv(r, 8),
  }));

  // 鐝骇鏍囧噯鍖?  records.forEach(r => {
    r.cls = r.cls
      .replace(/^淇℃伅宸ョ▼/, '淇℃伅')
      .replace(/^鐢靛瓙淇℃伅宸ョ▼/, '鐢典俊')
      .replace(/^閫氫俊宸ョ▼/, '閫氫俊')
      .replace(/^闆嗘垚鐢佃矾/, '闆嗙數');
  });

  // 鎺掑簭锛堟寜鎷奸煶锛?  records.sort((a, b) => {
    const ma = a.cls.match(/^([^\d]+)(\d+)$/);
    const mb = b.cls.match(/^([^\d]+)(\d+)$/);
    if (ma && mb) {
      const cmp = ma[1].localeCompare(mb[1], 'zh-CN');
      return cmp !== 0 ? cmp : parseInt(ma[2],10) - parseInt(mb[2],10);
    }
    return a.cls.localeCompare(b.cls, 'zh-CN');
  });

  // ========== D. 鍐欏洖鏁版嵁锛堝彧鏀箆alue锛宻tyle涓嶅姩锛?==========
  for (let i = 0; i < records.length; i++) {
    const row = ws.getRow(dataRows[i]);
    row.getCell(1).value = i + 1;  // 閲嶆柊缂栧彿
    row.getCell(2).value = '閫氫俊涓庝汉宸ユ櫤鑳藉闄€侀泦鎴愮數璺闄?;  // 缁熶竴瀛﹂櫌
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

// ========== 绛涢€夌増锛?2鍙?锛?==========
// 鍚屼笂 + 鍒犻櫎涓棿琛?+ 淇鍚堝苟
async function processFiltered(inputFile, outputFile) {
  const wb = new ExcelJS.Workbook();
  await wb.xlsx.readFile(inputFile);
  const ws = wb.getWorksheet(1);
  const merges = ws.model.merges ? [...ws.model.merges] : [];

  // ... 鍚屾牱璇诲唴瀛樸€佽瘑鍒銆佹彁鍙栨暟鎹€佹爣鍑嗗寲銆佹帓搴?...

  // 绛涢€夛細淇濈暀22鍙?锛屾帓闄?1鍙?  function isDate21(t) {
    if (!t) return false;
    const s = String(t).trim();
    return /21[鍙锋棩]/.test(s) || /21[鏅氭棭涓笅澶滅偣鏃跺垎]/.test(s);
  }
  const keep = records.filter(r => {
    const t = r.returnTime;
    if (!t || String(t).trim() === '') return true;
    if (isDate21(t)) return false;
    return true;
  });

  // 鍐欐暟鎹埌鍓?N 琛?  // 鍒犻櫎涓棿澶氫綑琛岋紙浠庝笅寰€涓婏級
  const firstDel = dataRows[0] + keep.length;
  const lastDel = tailRows[0] - 1;
  if (firstDel <= lastDel) {
    for (let r = lastDel; r >= firstDel; r--) ws.spliceRows(r, 1);
  }

  // 淇鍚堝苟鍗曞厓鏍硷紙姹囨€昏鍚堝苟璋冩暣鍒版柊琛屽彿锛?  if (merges.length > 0) {
    const newLastRow = ws.rowCount;
    const newMerges = [];
    for (const m of merges) {
      const ms = typeof m === 'string' ? m : '';
      const parts = ms.match(/^([A-Z]+)(\d+):([A-Z]+)(\d+)$/);
      if (parts) {
        const r2 = parseInt(parts[4], 10);
        if (r2 > dataRows[dataRows.length-1]) {
          // 灏鹃儴鍚堝苟璋冩暣鍒版柊鏈€鍚庝竴琛?          newMerges.push({ start: { row: newLastRow, col: 1 }, end: { row: newLastRow, col: 8 } });
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

## 鍏抽敭瑕佺偣
1. **姘歌繙鐢?`exceljs`**锛屼笉瑕佺敤 `xlsx`锛圫heetJS锛夌殑 `aoa_to_sheet`
2. **鍙敼 `.value`**锛屼笉鏀?`.style`锛屾牱寮忚嚜鐒朵繚鐣?3. 鍏堣鎵€鏈夋暟鎹埌鍐呭瓨鍐嶅鐞嗭紝閬垮厤璇诲啓浜ゅ弶
4. `spliceRows` 鍒犻櫎琛屾椂**浠庝笅寰€涓?*鍒狅紝閬垮厤琛屽彿鍙樺寲
5. 鍒犻櫎琛屽悗瑕?*鎵嬪姩淇鍚堝苟鍗曞厓鏍?*鐨勫紩鐢?6. 姹囨€昏濡傛灉琚竻绌轰簡鍊艰琛ュ洖 A 鍒楋紝骞堕噸鏂?merged
7. 鐝骇鏍囧噯鍖栬鍒欐寜闇€璋冩暣锛氫俊鎭伐绋嬧啋淇℃伅銆佺數瀛愪俊鎭伐绋嬧啋鐢典俊銆侀€氫俊宸ョ▼鈫掗€氫俊銆侀泦鎴愮數璺啋闆嗙數
