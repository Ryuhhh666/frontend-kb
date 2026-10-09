# 事件循环与宏微任务

## 题目
解释 JavaScript 的事件循环（Event Loop）机制，宏任务与微任务的区别是什么？请说明下面代码的输出顺序：

``js
console.log(1);
setTimeout(() => console.log(2));
Promise.resolve().then(() => console.log(3));
console.log(4);
``

## 解析
JS 是单线程的，同步代码在调用栈执行完后，事件循环先清空**微任务队列**（Promise.then、queueMicrotask、MutationObserver），再取**一个宏任务**（setTimeout、setInterval、I/O、UI 渲染）执行，执行后又清空微任务，如此循环。
输出顺序：`1 → 4 → 3 → 2`。同步代码先打印 1、4；then 回调作为微任务先于 setTimeout 宏任务执行。

## 知识点回顾
- 调用栈、任务队列、微任务队列的关系
- 常见宏任务：setTimeout、setInterval、I/O、UI rendering
- 常见微任务：Promise.then/catch/finally、queueMicrotask
- async/await 本质是 Promise + 微任务
