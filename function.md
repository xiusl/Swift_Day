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



