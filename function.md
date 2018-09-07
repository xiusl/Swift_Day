#### 定义和调用

```swift
func greet(person: String) -> String {
    let greeting = "Hello, \(person)."
    return greeting
}

print(greet(person: "Christ"))

func greetAgain(person: String) -> String {
    return "Hello again, " + person + "."
}
print(greetAgain(person: "Anny"))
```

#### 无形参函数

```swift
func sayHelloWorld() {
    return "hello world"
}
print(sayHelloWorld())
```

#### 多形参函数

```swift
func greet(person: String, alreadyGreeted: Bool) {
    if alreadGreeted {
        return greetAgain(person: pserson)
    } else {
        return greet(person: person)
    }
}
```

* `greet(person:)` 和 `greet(person:alreadyGreeted:)` 的函数名都为 `greet` 但却不是一个函数。

#### 无返回值函数

```swift
func greet(person: String) {
    print("hello, \(pserson).")
}
greet()
```

* 实际 `greet` 虽然没有明确定义返回值，还是有返回一个特殊类型 `Void` ，一个空元组，写作 `()` 。

#### 多返回值函数

* 使用元祖类型作为返回值类型。

```swift
func minMax(array: [Int]) -> (min, max) {
    var currentMin = 0
    var currentMax = 0
    for value in array {
        if currentMin > value {
            currentMin = value
        }
        if currentMax < value {
            currenrMax = value
        }
    }
    return (currentMin, currnetMax)
}

let bounds = minMax([4, 5, 12, 54, 2, 77, 9])
print("min is \(bounds.min), max is \(bounds.max).")
```

* 元组的成员值不需要在函数返回的时候命名，而是在函数返回值的时候就已经确定。

#### 可选元组返回类型

* 如果元组在函数返回值中可能 **没有值**，可以用一个 `可选` 元组返回类型来说明整个元组可能为 `nil` 。
* 书写方法为在可选元组类型的圆括号后面加 `?` ，`(Int, Int)?` 。

```swift
func minMax(array: [Int]) -> (min, max)? {
    if array.isEmpty {
        return nil
    }
    var currentMin = 0
    var currentMax = 0
    for value in array {
        if currentMin > value {
            currentMin = value
        }
        if currentMax < value {
            currenrMax = value
        }
    }
    return (currentMin, currnetMax)
}
```

#### 实际参数标签和形式参数名

* 每个**形式参数**都包含**实际参数标签**和**形式参数名**。
* **实际参数标签**在调用函数的时候使用，每一个**实际参数**前都要有实际**参数标签**。
* **形式参数名**在函数实现中使用，默认**形式参数**使用**形式参数名**作为**实际参数标签**。

```swift
func someFunction(firstParamName: Int, secondParamName: Int) {
    // 使用 firstParamName 和 secondParamName
}
someFunction(firstParamName: 1, secondParamName: 2)
```

#### 指定实际参数标签

```swift
func someFunction(argumentLabel argumentName: Int) {
    // 使用 argumentName
}
someFunction(argumentLabel: 1) // 使用 argumentLabel
```

* 当为形式参数提供了实际参数标签，在调用的时候就必须使用实际参数标签。

```swift
func greet(person: String, from hometown: String) -> String {
    return "hello \(person), glad you cloud visit from \(hometown)."
}
greet(person: "Bill", from: "Beijign")
```

#### 省略实际参数标签

* 使用 `-` 为**形式参数**来代替显式的**实际参数标签**。

```swift
func someFunction(_ firstParamName: Int, secondParamName: Int) {
    // 使用 firstParamName、secondParamName
}
someFunction(1, secondParamName: 2)
```

#### 默认的形式参数值

* 在形式参数类型后为形式参数指定一个默认的值。
* 在调用函数的时候存在默认值的形式参数可以省略。

```swift
func someFunction(paramName: Int = 1) {
    return paramName
}

print(someFunction(12)) // 12
print(someFunction())   // 1
```

#### 可变形式参数

* 一个可变形式参数可以接受零个或多个特定的值。
* 可变形式参数是在参数类型后插入 `...` 来定义。
* 一个函数只能有一个可变形式参数。

```swift
func arithmeticMean(_ numbers: Double...) -> Double {
    var total: Double
    for number in numbers {
        total += number
    }
    return total / Double(numbers.count)
}
arithmeticMean(1, 3, 5, 6)
arithmeticMean(1.2, 23.4.25, 2.5, 21.0)
```

#### 输入输出形式参数

* 在函数内修改一个形式参数的值，在函数结束后改变依然生效。
* 在形式参数的类型前使用 `inout` 。
* 只能把变量作为输入输出的实际参数。
* 在函数调用的时候在实际参数前使用 `&` 来明确是可以被函数修改的。

```swift
func swapTwoInts(_ a: inout Int, _ b: inout Int) {
    let temporary = a
    a = b
    b = temporary
}

var someInt = 6
var anotherInt = 8
swapTwoInts(&someInt, &anotherInt)
print("someInt is \(someInt), anotherInt is \(anotherInt).")
// someInt is 8, anotherInt is 6.
```

#### 函数类型

* 由形式参数类型，返回类型组成。

```swift
func addTwoInts(_ a: Int, _ b: Int) -> Int {
    return a + b
}
func mutiplyTwoInts(_ a: Int, _ b: Int) -> Int {
    return a * b
}
// 函数类型 (Int, Int) -> Int


func printHelloWorld() {
    print("hello world")
}
// 函数类型 () -> Void
```

#### 函数类型的使用

```swift
var mathFunction: (Int, Int) -> Int = addTwoInts
print(mathFunction(2, 3)) // 5

metahFunction = mutiplyTwoInts
print(mutiplyTwoInts(2, 3) // 6

// 使用 Swift 的类型推断
let anotherMathFunction = addTwoInts
```

#### 函数类型作为形式参数类型

```swift
func printMathResult(_ mathFunction: (Int, Int) -> Int, _ a: Int, _ b:Int) {
    print("Result: \(mathFunction(a, b))")
}
printMathResult(addTwoInts, 2, 3) // Result: 5
```

#### 函数类型作为返回类型

```swift
func setForward(_ input: Int) -> Int {
    return input + 1
}
func setBackward(_ input: Int) -> Int {
    return input - 1
}

func chooseStepFunction:(backwards: Bool) -> (Int) -> Int {
    return backwards ? setForward : setBackward
}

var currentNum = 3
let moveNearerToZero = chooseStepFunction(backwards: currentNum > 0)
while currentNum > 0 {
    print(currentNum)
    currentNum = moveNearerToZero(currentNum)
}
print(currentNum)
// 3
// 2
// 1
// 0
```

#### 内嵌函数

```swift
func chooseStepFunction:(backwards: Bool) -> (Int) -> Int {
    func setForward(_ input: Int) -> Int { return input + 1 }
    func setBackward(_ input: Int) -> Int { return input - 1 }
    return backwards ? setForward : setBackward
}
var currentNum = -3
let moveNearerToZero = chooseStepFunction(backwards: currentNum > 0)
while currentNum > 0 {
    print(currentNum)
    currentNum = moveNearerToZero(currentNum)
}
print(currentNum)
// -3
// -2
// -1
// 0
```



