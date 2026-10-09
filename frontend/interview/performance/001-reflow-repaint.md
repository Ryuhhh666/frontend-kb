# 重排与重绘

## 题目
什么是重排（reflow）和重绘（repaint）？如何减少它们对性能的影响？

## 解析
**重排**：元素几何属性（位置、尺寸）变化，浏览器需重新计算布局，代价高；**重绘**：仅视觉属性（颜色、背景）变化，重新绘制但不重排。重排必然引发重绘。优化手段：1) 批量修改 DOM（使用 DocumentFragment 或一次性 innerHTML）；2) 读写分离，避免交替读写触发强制同步布局；3) 使用 `transform`、`opacity` 做动画（只触发合成，跳过布局与绘制）；4) 对频繁 resize/scroll 用节流防抖；5) 使用 `will-change` 提升合成层。

## 知识点回顾
- 渲染流水线：JS → Style → Layout → Paint → Composite
- 强制同步布局（layout thrashing）的成因
- 合成层与 GPU 加速
- requestAnimationFrame 与动画优化
