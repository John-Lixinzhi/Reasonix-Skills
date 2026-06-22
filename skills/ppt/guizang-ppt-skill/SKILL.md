---
name: guizang-ppt-skill
description: [PPT] 归藏网页PPT — USE when 需要HTML网页PPT/演讲Slides/发布会演示。DO 生成横向翻页HTML，A电子杂志风/B瑞士国际主义风。NOT for 需要PPTX文件（用ppt-master）。Triggers: 做PPT/演示/演讲/幻灯片/slides/网页PPT
---

# 归藏网页 PPT (guizang-ppt-skill)

生成**单文件 HTML 横向翻页 PPT**。源仓库：D:\guizang-ppt-skill-main

## 两种风格

### 风格 A · 电子杂志风（默认）
- WebGL 流体背景 + 衬线标题(Noto Serif SC + Playfair Display)
- 10 种布局：封面、章节、数据大字报、图文、图片网格、Pipeline、对比等
- 5 套主题：墨水经典、靛蓝瓷、森林墨、牛皮纸、沙丘
- 适合：人文分享、行业观察、商业发布、"杂志感"演讲

### 风格 B · 瑞士国际主义风
- WebGL 极细网格 + 全程无衬线(Inter + Helvetica + Noto Sans SC)
- 22 种锁定版式(S01-S22)，不可发明新结构
- 4 套锚点色：克莱因蓝IKB、柠檬黄、柠檬绿、安全橙
- 适合：科技产品、数据汇报、工程/设计分享、年度总结

## 工作流
1. **需求澄清** — 7问：风格/受众/时长/素材/图片/主题色/硬约束
2. **拷贝模板** — 从 D:\guizang-ppt-skill-main\assets\template.html 或 template-swiss.html
3. **选主题色** — 从 references/themes.md 或 themes-swiss.md 选，不允许自定义
4. **填充内容** — 从 layouts.md 或 layouts-swiss.md 挑布局，不要从零写
5. **自检** — 对照 references/checklist.md，P0 必须全过；瑞士风运行 validate-swiss-deck.mjs
6. **预览** — 浏览器直接打开 index.html

## 关键约束
- 风格 A 和 B **不能混用**
- 类名必须在模板 `<style>` 里有定义，不要发明新类
- 图片用标准比例(21:9/16:10/16:9/4:3/3:2)，不要原图奇葩比例
- 瑞士风大字字重 200(ExtraLight)，越大越细
- 瑞士风不允许渐变/阴影/圆角
- 每页一个语义化动效 recipe，不是统一 fade-up

## 核心文件位置
- 模板：D:\guizang-ppt-skill-main\assets\template.html / template-swiss.html
- 布局参考：D:\guizang-ppt-skill-main\references\layouts.md / layouts-swiss.md
- 主题色：D:\guizang-ppt-skill-main\references\themes.md / themes-swiss.md
- 校验器：D:\guizang-ppt-skill-main\scripts\validate-swiss-deck.mjs
- 质量清单：D:\guizang-ppt-skill-main\references\checklist.md
