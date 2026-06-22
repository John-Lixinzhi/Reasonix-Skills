---
name: humanize-skill
description: [参考] AI去味检测 — USE when 需要检测/降低文本的AI痕迹/写论文投稿前自查。DO humanize(去AI味9杠杆) + ai-check(取证级检测评分)。NOT for 英文以外语言效果有限。Triggers: 去AI味/humanize/查AI率/降重/文本检测/改写得更像人写的
---

# AI 去味 & 检测

来源：harshaneel/humanize (45⭐)，50+ 篇同行评审文献支撑

## 两个技能

### humanize — 去 AI 味
9 个去 AI 杠杆：困惑度注入、突发性强化、修饰词手术、结构化扁平化、具体化插入、语音与语域、AI过渡移除、标点规范化、RLHF语音剥离

### ai-check — AI 检测
取证级分析，9 个信号类别评分，逐条标注证据引用，输出裁决 + 置信度 + AI编辑比例估计

## 基准测试
- 25 种不同语域测试，全部落在 Human / Likely Human 范围
- 外部验证（Binoculars 交叉困惑度）：全部越过人类阈值
- 注意：对 GPTZero/Grammarly 等学习的分类器效果有限（需混合策略）

## 对我生态的价值
- 写科研论文/投稿前自查 AI 率
- 与 research-writing 配合使用
