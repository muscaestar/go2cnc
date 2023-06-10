# 类型
类型内容比较多，这里记录一些干Java的时候不会遇到的知识点

## 复数 complex
Go原生支持复数类型complex64，complex128。复数有两部分组成：`c = a + bi` 中，复数c的实数部分为a，虚数部分为b。复数只在矢量运算中会使用。

## 自定义类型、类型别名
```go
type newInt int // 自定义类型
type aliasInt = int // 类型别名

var oneInt int = 1
res := aliasInt(1) == oneInt // true
newInt(1) == oneInt // 无法编译  (mismatched types newInt and int)
```
- 上述例子中，newInt是一个基于int类型的新类型，无法直接与int型比较
- 类型别名指代的就是该类型，因此别名与原类型可以互相比较
