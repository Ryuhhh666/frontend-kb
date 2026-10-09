# 手写防抖 debounce

## 题目
手写一个防抖（debounce）函数，并说明它和节流（throttle）的区别。

## 解析
``js
function debounce(fn, delay) {
  let timer = null;
  return function (...args) {
    clearTimeout(timer);
    timer = setTimeout(() => fn.apply(this, args), delay);
  };
}
``
防抖：事件停止触发 delay 毫秒后才执行一次，适合搜索框输入联想、窗口 resize 结束后计算。节流：固定时间间隔内最多执行一次，适合滚动监听、按钮防连点。

## 知识点回顾
- 闭包保存 timer 状态
- `fn.apply(this, args)` 保证 this 指向和参数透传
- 进阶：支持立即执行（leading）、取消、返回值
- requestAnimationFrame 实现节流的思路
