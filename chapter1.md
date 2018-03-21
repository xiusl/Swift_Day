# 0x01

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

使用 **\[\]** 来声明字典和数组

```
var nameList = ["jim", "tom", "frank", "wallte"]
nameList[1] = "shilin"

var person = [
    "name": "frank",
    "phone": "123132"
]
person["sex"] = "male"
```

创建空的数组、字典

```
let emptyArr = [String]()
let emptyDict = [String: Float]()

// 如果类型是可推断的
var nameList = []
var person = [:]
```

使用 `if` 和  `switch` 进行条件控制，`for-in` 、`while` 和 `repeat-while` 进行循环控制

判断、循环条件的圆口号 **\(\)** 是可选的，但判断、循环体的花括号 **{}** 是必须的

```
let scores = [75, 43, 102, 90, 22]
var teamScore = 0
for socre in scores {
    if socre > 50 {
        teamScore += 3
    } else {
        teamScore += 1
    }
}
print(teamScore) // 11
```

在 `if` 的条件中的类型必须是 `Boolean`

```
if source { // error 不会默认的和零比较
    // ...
}
```

可以使用 `if` 和 `let` 一起来处理值可能为空的情况，这些值相当于可选值，一个可选值要么存在一个值要么为空 `nil` ，使用 `?` 来标记一个变量的值是可选的

```
var optionalStr: String? = "Hello"
print(optionalStr == nil)

var optionalName: String? = "xiu"
// optionalName = nil
var greeting = "Hello"
if let name = optionalName {
    greeting = "Hello, \(name)"
    print(greeting)
} else {
    print(greeting)
}
```

`switch` 支持任何类型的数据，在匹配到对应的 `case` 中，不需要明确的 `break` 来跳出

```
let vegetable = "red pepper"
switch vegetable {
    case: "celery": 
        print("Add some raisins and make ants on a log.")
    case: "cucumber", "watercress":
        print("That would make a good tea sandwich")
    case: let x where x.hasSuffix("pepper"):
        print("Is it a spicy \(x)?")
    default:
        print("Everythin tastes good in soup.")
}
```

使用 `for-in` 变量字典中的元素，可以同时得到 `key & value` ，字典是一个无序集合，遍历的顺序也是随机的

```
let interestingNumbers = [
    "Prime": [2, 3, 5, 7, 11],
    "Firbonacci": [1, 1, 2, 3, 5, 8],
    "Square": [1, 4, 5, 9, 16, 25],
]
var largest = 0
for (kind, numbers) in interestingNumbers {
    for number in numbers {
        if number > largest {
            largest = number
        }
    }
}
print(largest)
```

使用 `while` 可以重复执行一段代码直到条件改变，循环条件可以在代码块最后出现，保证代码块至少执行一次

```
var n = 2
while n < 100 {
    n *= 2
}
print(n)

var m = 2
repeat {
    m *= 2
} while m < 100
print(m)
```

使用 `..<` 可以生成指定范围的索引， `..<` 不包含结尾， `...` 包含结尾

```
var total = 0
for i in 0..<4 {
    total += i
}
print(total)
// 0..<4 -> 0 1 2 3
// 0...4 -> 0 1 2 3 4
```

使用 `func` 定义函数，使用 `funcName(param1:"",param2:"",...)` 调用函数，使用 `->` 来指定函数的返回值类型

```
func greet(person:String, day:String) -> String {
    return "Hello \(person), today is \(day)"
}
greet(person:"xiu", day:"Tuesday")
```

使用 `_` 来指定不需要参数名，使用 ``` \(空格\)来指定内部参数名和外部参数名``on day\`

```
// on 为外部参数名，day 为内部参数名
func greet(_ person:String, on day:String) -> String {
    return "Hello \(person), today is \(day)"
}
greet("xiu", on:"Tuesday")
```

使用元组来返回多个混合的值

```
func calculateStatistics(scores: [Int]) -> (min: Int, max: Int, sum: Int) {
    var min = scores[0]
    var max = scores[0]
    var sum = 0
    for score in scores {
        if score > max {
            max = score
        } else if score < min {
            min = score
        }
        sum += score
    }
    return (min, max, sum)
}
let statistics = calculateStatistics(scores:[5, 3, 100, 3, 9])
print(statistics.sum)
print(statistics.min)
print(statistics.max)
```

函数可以嵌套使用，里层函数可是使用外层定义的变量，可以使用嵌套函数来组织冗长、复杂的代码

```
func returnFifteen () -> Int {
    var y = 5
    func add() {
        y += 10
    }
    add()
    return y
}
returnFifteen()
```

函数作为一种对象，可以作为另一个函数的返回值或参数

```
// 返回值
func makeIncrementer () -> ((Int)->Int) {
    func add (number: Int) -> Int {
        return 1 + number
    }
    return add
}
var incrementer = makeIncrementer()
incrementer(7)
// 参数
```



