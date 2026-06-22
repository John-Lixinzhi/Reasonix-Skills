---
name: skill-onboarder
description: [system] Skill onboarder - USE when installing new skill/importing skill. DO fetch, analyze, install_skill, update catalog. NOT for modifying existing. Triggers: install/new skill/onboard/import/add skill
---

# Skill Onboarder — 新技能接入专员

我是技能"HR部门"，负责把每个新 skill 按标准流程融入生态。

## 触发条件

- 用户说"装个新skill" / "安装XX技能" / "导入这个skill"
- 用户给了 GitHub 地址或 skill 内容，要求装到 Reasonix
- 用户说"把这个加到生态里"
- 新 skill 需要配置触发场景、分类、依赖关系

## 接入标准流程

### Step 1 · 获取源码
- 如果是 GitHub 仓库 → 用 GitHub MCP 获取内容，或下载 ZIP 到 D:\
- 如果是直接给的文本 → 读取内容
- 确定 skill 的核心文件（SKILL.md / README / 主文件）

### Step 2 · 分析分类
- 它属于哪个领域？研发/数据/办公/设计/工具/系统/...
- 它的触发场景是什么？什么情况应该自动调用？
- 它和现有 skill 有没有重叠/冲突？
- 它依赖其他 skill 吗？
- 有没有明确不该用它的场景（负样本）？

### Step 3 · 安装到 Reasonix
- 用 `install_skill` 创建 Reasonix skill
- description 按标准格式：`[分类] 名称 — 触发条件：xxx。作用：xxx`
- 如果是大型项目（有模板/参考文件），同时克隆到 D:\

### Step 4 · 更新目录
- 打开 `SKILLS_CATALOG.json`
- 添加新条目：name / description / category / tags / triggers / negative_samples / dependencies / priority
- 确认没有分类冲突

### Step 5 · 汇报
- 告诉用户装好了
- 给出：技能名称 / 分类 / 触发条件 / 和现有生态的关系 / 调用方式
