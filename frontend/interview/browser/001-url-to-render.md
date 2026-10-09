# 输入 URL 到页面渲染

## 题目
从输入 URL 到页面渲染完成，中间经历了哪些主要阶段？

## 解析
1) **DNS 解析**：缓存查询 → 递归/迭代查询拿到 IP；2) **建立连接**：TCP 三次握手（HTTPS 还有 TLS 握手）；3) **发送 HTTP 请求**并接收响应（涉及缓存：强缓存/协商缓存）；4) **解析渲染**：HTML 解析构建 DOM，CSS 构建 CSSOM，合成渲染树 → 布局（Layout）→ 绘制（Paint）→ 合成（Composite）；5) JS 执行会阻塞 HTML 解析（script 默认），async/defer 可改变加载行为。

## 知识点回顾
- DNS 缓存层级：浏览器 → 系统 → 路由器 → ISP
- 强缓存（Cache-Control/Expires）与协商缓存（ETag/Last-Modified）
- 重排（reflow）与重绘（repaint）的区别及优化
- script 标签的加载执行：默认 / async / defer
