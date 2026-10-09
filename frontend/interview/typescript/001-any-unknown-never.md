# any / unknown / never

## 题目
`any`、`unknown`、`never` 三者的区别是什么？分别在什么场景下使用？

## 解析
- `any`：放弃类型检查，可赋给任何类型也可从任何类型赋值，等同于关闭类型系统，应尽量避免。
- `unknown`：类型安全的 any，可以接收任何值，但使用前必须收窄（typeof、instanceof、类型断言），适合处理外部不可信输入（如 JSON.parse 结果）。
- `never`：表示永远不会出现的类型，是所有类型的子类型，用于函数永不返回（抛错、死循环）或穷尽性检查（switch 处理所有分支后兜底）。

## 知识点回顾
- 类型兼容性：`never < unknown < any` 的可赋值关系
- 类型收窄（narrowing）手段：typeof、instanceof、in、字面量判等
- 穷尽性检查：`default` 分支赋值 `never` 捕漏
- 泛型、条件类型与 never 的配合（如 Exclude 的实现）
