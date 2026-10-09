# React 与 Vue 的更新机制

## 题目
React 和 Vue 的响应式 / 更新机制有什么本质区别？

## 解析
React 采用**不可变数据 + 重新渲染**：setState 触发组件函数重新执行，通过虚拟 DOM diff 计算变更，默认父组件更新会带动子组件重渲（需 memo、useMemo 等手动优化）；React 18+ 引入并发渲染可中断更新。Vue（3.x）采用**响应式追踪**：基于 Proxy 劫持数据读写，组件渲染时收集依赖，数据变化时精准通知对应组件更新，天然细粒度，优化成本更低。

## 知识点回顾
- React：Fiber 架构、reconciliation、虚拟 DOM diff 策略（key 的作用）
- Vue：Proxy 响应式原理、依赖收集与触发、编译时优化（patchFlag、静态提升）
- 两者性能优化手段对比：React 手动 memo vs Vue 自动依赖追踪
- 状态不可变（immutability）在 React 中的意义
