---
name: ppt-master
description: [PPT] PPT大师 — 触发条件：需要生成可编辑的PPTX文件/需要图表/H5演示文稿时。使用pptxgenjs生成精确控制每个元素位置的PPTX。双受众模式：工程师版(技术原理+代码)+管理者版(ROI分析+策略)。17种配色方案+9种布局+视觉QA
---

# PPT Master (ai-ppt-master-skill)

生成**可编辑的 PPTX 文件**（不是HTML），通过 pptxgenjs 精确控制每个元素位置。

## 核心能力
- **精确控制**：不是提示词模板，是用脚本控制 PPT 元素位置、颜色、字体、图表
- **双受众模式**：工程师版（技术原理+代码示例）/ 管理者版（ROI分析+落地策略）
- **自动图表**：柱状图、折线图、雷达图

## 生成流程
1. **大纲生成** — 用大模型做创意或技术深度路线
2. **内容填充** — 双受众模板
3. **插图** — AI 生成配图
4. **图表** — ppt-charts.js / ppt-charts.py
5. **PPT构建** — pptxgenjs (generate-ppt.js)
6. **视觉QA** — 按设计规范检查

## 设计要求
- 禁 AI 垃圾风：禁紫色渐变、禁 Arial/Inter、禁全圆角卡片
- 色彩有态度：主色 60-70%、辅色 20-25%、强调色 5-10%
- 每页必须经过视觉 QA 检查

## 依赖
- npm install pptxgenjs
