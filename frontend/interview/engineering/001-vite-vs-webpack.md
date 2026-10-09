# Vite 与 Webpack

## 题目
Vite 为什么比传统的 Webpack 开发模式快？其生产构建为什么又选择了 Rollup？

## 解析
**开发阶段**：Webpack 需要从入口递归打包整个模块图后才能启动；Vite 利用浏览器原生 ESM，按需编译——浏览器请求某个模块时才即时转换该模块（esbuild 预构建依赖），启动几乎与项目大小无关，HMR 也只更新单个模块。**生产构建**：Vite 使用 Rollup，因为 Rollup 基于 ESM 的静态分析，Tree-shaking 更彻底、产物更精简，适合输出库和最终产物；esbuild 打包功能当时生态兼容性（代码分割等高级特性）尚不完整。

## 知识点回顾
- 浏览器原生 ESM 与 CommonJS 的差异
- esbuild（Go 编译）与 Rollup（ESM 静态分析）各自优势
- HMR 原理：模块图局部更新 + websocket 推送
- Tree-shaking 生效条件：ESM 静态结构、无副作用标记（sideEffects）
