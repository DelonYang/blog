---
title: "Javascript 学习"
date: 2019-03-07T15:38:54+08:00
---

# Javascript 学习
终于开始Javascript学习了！

## 类型
常见的js类型：

- Number
- String
- Boolean
- Symbol
- Object
    - Function
    - Array
    - Date
    - RegExp
    - Error
- Null
- Undefined

### Number
Number包括了整型、单精度、双精度；
计算时候容易出现脑残问题：`0.1 + 0.2 = 0.30000000000000004`.

常用函数：

```javascript
// 字符串 -> 整数
parseInt('100', 10)

// 字符串 -> 浮点数
parseFloat('1.5')
```