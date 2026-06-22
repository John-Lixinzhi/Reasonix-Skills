---
name: ppt-motion
description: [ppt] Motion & animation - USE when need smooth transitions/slide animations. DO control transitions, entry animations, background micro-motion. NOT for static PPTs. Triggers: animation/transition/motion/smooth
---

# PPT 转场与动效指南

配合 guizang-ppt-skill 使用，让生成的 HTML PPT 具有丝滑转场和动态效果。

## 一、翻页转场（Slide Transition）

### 在 template 中实现
guizang 模板已内置 `#deck` 容器的 transition：
```css
#deck{transition:transform .9s cubic-bezier(.77,0,.175,1)}
```
这个缓动曲线是"慢-快-慢"的丝滑效果，0.9s 是最舒服的时长。

### 可叠加的过渡增强
在 `#deck` 容器上加一个 overlay 遮罩，翻页时淡入淡出：
```css
/* 在 deck 和 slide 之间加一层 */
#deck::after {
  content:''; position:fixed; inset:0; z-index:5;
  background:var(--paper);
  pointer-events:none;
  opacity:0;
  transition:opacity .4s ease;
}
body.transitioning #deck::after { opacity:.3 }
```

### 缓动曲线推荐
| 效果 | cubic-bezier | 适用 |
|------|-------------|------|
| 丝滑标准 | `.77,0,.175,1` | 默认翻页 |
| 更软 | `.83,0,.17,1` | 叙事型PPT |
| 弹性 | `.34,1.56,.64,1` | 创意型（慎用） |
| 干脆 | `.25,.46,.45,.94` | 数据型 |

## 二、入场动画（Entry Animation）

guizang 模板已集成 Motion One，每页可加独立 `data-anim`：

### 主要动画类型
- `fade-up` — 从下往上淡入（最常用）
- `fade-left` / `fade-right` — 从侧边滑入
- `scale-in` — 缩放弹入（适合数字/大字报）
- `stagger` — 列表项逐个交错出现
- `reveal` — 遮罩展开

### 每页一个语义化动效
- 封面 → 大标题 `scale-in` + 副标题 `fade-up`（延迟）
- 数据页 → 数字 `scale-in` + 图表 `stagger`
- 图文页 → 图片 `fade-left` + 文字 `fade-right`
- 章节页 → 大字 `reveal`

**不能所有页用同一个 animation recipe。**

## 三、背景微动（Background Motion）

模板有 WebGL 背景已经带了流体/网格动画。
额外可以加的：
- **视差** — 背景 `transform:translateY()` 速度是前景的一半
- **呼吸光晕** — 强调色 radial-gradient 缓慢变化 opacity
- **微颗粒** — CSS 粒子层缓慢移动

## 四、动效 QA 清单
- [ ] 翻页过渡是否丝滑（不是卡顿跳变）
- [ ] 每页有独立的入场动效
- [ ] 动效不过度（不炫技，不干扰阅读）
- [ ] 动画时长合理（入场 0.3-0.6s，过渡 0.7-0.9s）
- [ ] 低性能模式有降级方案（B键切换）
- [ ] 所有内容最终都能静态展示（动画不依赖 JS）
