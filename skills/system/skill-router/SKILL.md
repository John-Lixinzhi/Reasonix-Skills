---
name: skill-router
description: [system] Skill router - USE when multiple skills match/unsure which to use. DO analyze request, query catalog, recall, rerank, execute. NOT for known single skill. Triggers: which skill/router/not sure/help choose
---

# Skill Router — 技能路由管理器

## 定位
我是所有技能的"经理人"。当你面对大量技能不确定用哪个时，由我来做路由决策。

## 触发条件
- 用户请求可能命中多个技能
- 你不太确定用哪个技能最合适
- 技能数量超过 5 个，需要缩小选择范围
- 用户明确说"用合适的技能处理"

## 工作流程

### 1. 读目录
读取 `SKILLS_CATALOG.json` 了解所有技能的分类、标签、触发场景和负样本

### 2. 分析请求
从用户请求中提取：
- 核心意图（要做什么）
- 领域（开发/数据/设计/工具/学习）
- 技术栈（Python/JS/Go...）
- 排除信号（明显不相关的领域）

### 3. 召回候选
用语义匹配从目录中召回 top-3 到 top-5 候选技能

### 4. 重排选择
从候选中选出最匹配的 1 个技能，给出理由

### 5. 执行或链式调用
- 如果 1 个技能够用 → 调用它
- 如果需要多个技能协作 → 按 SKILLS_CATALOG 中的 dependencies 链式调用
