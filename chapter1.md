# Day01

使用`let`声明一个常量，使用`var`声明一个变量

```
let a = 10
var b = 20
b = 30
```

常量：在编译时不必须知道常量的值，一旦需要使用就必须要有明确的值

```
let a: Int
a = 10
```

变量或常量在赋值的时候必须要是同一类型，然而在初始化的时候不需要指定类型，编译器会自动判断类型。当初始化的值不能明确他的类型时，需要使用** : **来指定类型。

```
let s = "hello" // String
let a = 20 // Int
let b = 70.0 // Double
let c: Double = 30 //Double
```

变量和常量的值不会自动转换成其他类型\(没有隐式转换\)，如果需要类型转换，需要明确的指明目标类型

```
let s = "Hello"
let a = 100
let sa = s + String(a)
// if no String() -> Binary operator '+' cannot be applied to operands of type 'String' and 'Int'
```

有一种简单的方式把值拼接到字符串中，使用**\\(\)**

```
let a = 2
let b = 4
let s = "hello \(a) count"
let t = "hello \(a + b) count"
```

使用 **“”“** 可以声明多行的字符串\(**”“”**前后需要换行\)

```
let s = """
I said "hello".
And then I said "I belive peace & love" 
"""
```



