#### Desc

* 闭包是可以在你的代码中被传递和引用的功能性独立模块。
* Swift 中的闭包与 C，Objective-C 中的 block 很像。
* 闭包可以捕获和存储定义在其上下文中的任何变量和常量的引用（闭合并包裹）

#### 形式

* 全局函数是一个有名字但不会捕获任何值得闭包。
* 内嵌函数是一个有名字且能从其长层函数捕获值的闭包。
* 闭包表达式是一个轻量级语法所写的 可以捕获其上下文中常量或变量值  的没有名字的闭包。

#### 语法

```swift
{ (parameters) -> (return type) in
    statements
}
```

#### 简化语法

* 利用上下文推断形式参数和返回值类型。
* 单表达式的闭包可以隐式返回。
* 简写实际参数名。
* 尾随闭包语法。

#### Sorted 方法

```swift
let names = ["Chris", "Ewa", "Alias", "Tom"]

func backward(_ s1: String, _ s2: String) -> Bool {
    return s1 > s2
}
var reversedNames1 = names.sorted(by: backward)

var reversedNames2 = names.sorted(by: { (s1: String, s2: String) -> Bool in return s1 > s2 })

// 语境中推断类型
var reversedNames3 = names.sorted(by: { s1, s2 in return s1 > s2 })

// 单表达式隐式返回
var reversedNames4 = names.sorted(by: { s1, s2 in s1 > s2 })

// 简写实际参数名
var reversedNames5 = names.sorted(by: {$0 > $1})

// 运算符函数
var reversedNames6 = names.sorted(by: >)

// 尾随闭包
var reversedNames7 = names.sorted() {$0 > $1}
// 尾随闭包，函数的唯一实际参数传入
var reversedNames8 = names.sorted {$0 > $1}
```

#### map 方法

```swift
let digitNames = [
    0: "Zero", 1: "One", 2: "Two", 3: "Three", 4: "Four",
    5: "Five", 6: "Six", 7: "Seven", 8: "Eight", 9: "Nine"
]
let numbers = [12, 63, 90]
let strings = numbers.map {
    (number) -> String in
    var number = number
    var output = ""
    repeat {
        output = digitNames[number % 10]! + output
        number /= 10
    } while number > 0
    return output
}
print(strings)
```

#### 捕获值

* 闭包能够从上下文捕获已经定义的常量和变量。**即定义这些变量和常量的作用域已经不存在，闭包仍然可以在函数体中引用和修改这些值。**

```swift
func makeIncrementer(forIncrement amount: Int) -> () -> Int {
    var runTotal = 0;
    //    func incrementer() -> Int {
    //        runTotal += amount
    //        return runTotal
    //    }
    //    return incrementer
    return { () -> Int in
        runTotal += amount
        return runTotal
    }
}

let incrementByTen = makeIncrementer(forIncrement: 10)

print(incrementByTen())  // 10

print(incrementByTen())  // 20
```



