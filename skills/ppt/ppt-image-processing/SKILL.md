---
name: ppt-image-processing
description: [ppt] Image processing - USE when need boolean ops/image fill shapes/circular layout. DO shape merge, image fill, radial layout. NOT for text editing. Triggers: image/shape/boolean/photo edit
---

# PPT 图形图像处理

来源：PPT日记视频教程技能库

## 1. 形状拆分（布尔运算）
- 联合：多个形状合并
- 组合：合并减去重叠
- 拆分：按边界拆成独立形状
- 相交：只保留重叠部分
- 剪除：用第一个减去后面的
- 经典组合：文字+图片→相交=图片填充文字；大矩形-小矩形→剪除=边框

## 2. 图片填充形状
- 方法一：形状填充→图片或纹理填充
- 方法二：相交法（先选图片再选形状→相交）

## 3. 环形布局
- iSlide插件：选中元素→环形布局→设置数量/半径
- 手动：辅助圆+复制旋转（360÷数量），F4快速重复
- 元素建议3-12个

## 4. 图片透明度与亮度
- 透明度：设置图片格式→透明度0-100%
- 背景图片透明度30-70%
- 亮度/对比度：图片格式→校正
- 颜色：饱和度/色调/重新着色
