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

使用 **"""** 可以声明多行的字符串\(**"""**前后需要换行\)

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

使用 `_` 来指定不需要外部参数名，使用 ``` \(空格\)来指定内部参数名和外部参数名``on day\`

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
func returnFifteen() -> Int {
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
func makeIncrementer() -> ((Int)->Int) {
    func add (number: Int) -> Int {
        return 1 + number
    }
    return add
}
var incrementer = makeIncrementer()
incrementer(7)

// 参数
func hasAnyMatches(list: [Int], condition: (Int) -> Bool) ->Bool {
    for item in list {
        if condition(item) {
            return true
        }
    }
    return false
}
func lassThanTen(number: Int) -> Bool {
    return number < 10
}
var numbers = [20, 19, 7, 12]
hasAnyMatches(list: numbers, condition:lassThanTen)
```

函数闭包？？

```
var numbers = [20, 18, 2, 53]
numbers.map({ (number: Int) -> Int in
    let result = 3 * number
    return result
})
```

```
var numbwes = [20, 12, 3, 31]
let mappedNumbers = numbers.map({ number in 3 * number })
print(mappedNumbers)
```

```
let sortedNumbers = numbers.sorted { $0 > $1 }
print(sortedNumbers)
```

使用 `class` 关键字和类名来创建一个类，类属性的声明方式与常量、变量的声明方式相同，除了属性是在类中，同样的方法的声明方式和函数一样

```
class Shape {
	var numberOfSides = 0
	func simpleDescription() -> String {
		return "A shape with \(numbersOfSides) sides."
	}
	let count = 10
	func showAny(p: String) {
		print(p)
	}
}
```

使用类名+ `()` 创建类实例，使用 `.` 来访问类的属性、调用类方法

```
var shape = Shape()
shape.numberOfSides = 4
var shapeDesc = shape. simpleDescription()
```

上面的 `Shape` 类少了一个很重要的东西。当实例被创建的时候，需要一个初始化函数来初始化类中的一些值。使用 `init` 创建

```
class NamedShape {
	var numberOfSides: Int = 0
	var name: String
	
	init(name: String) {
		self.name = name
	}
	
	func simpleDescription() -> String {
		return "A shape with \(numbersOfSides) sides."
	}
}
```

注意 `self` 被用来区分属性中的 `name` 和 方法参数中的 `name` 。当你创建一个类的实例时，用于初始化的参数会像方法调用一样被传递。每个属性都必须被指定一个值，或者在属性声明的时候，或者在类实例初始化的时候

当你需要的在实例释放的时候清理一些资源的时候，使用 `deinit` 可以定义一个析构方法，他会在实例释放的时候调用

子类的声明是在类名后使用 `:` 链接父类名，类不是必须要有一个父类的，你可以根据需求来包括、删除父类

子类中的方法使用 `override` 关键字将会覆盖父类中相同方法的实现。如果意外地重写了父类的方法，并且没有使用 `override`，编译器将会报错。当子类中使用了 `override` 但父类中没有相应的方法时，编译器也会报错

```
class Circle: NamedShape {
	var radius: Double
	
	init(radius: Double, name: String) {
		self. radius = radius
		suprt.init(name: name)
		numberOfSides = 0
	}
	
	func area () -> Double {
		return radius * radius * M_PI
	}
	
	override func simpleDescription() -> String {
		return "A circle with radius of length \(radius)."
	}
}
let test = Circle(radius: 4.2, name: "Tesr circle")
test.area()
test.simlpeDescription()
```

除了包含简单的属性，类的属性还可以拥有 `getter` 、 `setter` 方法

```
class EquilateralTriangle: NamedShape {
	var sideLength: Double = 0.0
	
	init(sideLength: Double, name: String) {
		self.sideLength = sideLength
		super.init(name: name)
		numberOfSides = 3
	}
	
	var perimeter: Double {
		get {
			return 3.0 * sideLength
		}
		set {
			sideLength = newValue / 3.0
		}
	}
	
	override func simpleDescription() -> String {
		return "An equilateral triangle with sides of length\(sideLength)."
	}
}
var triangle = EqauilateralTriangle(sideLength: 2.1, name: "a Triangle")
print(triangle.perimeter)
triangle.perimeter = 12.9
print(triangle.sideLength)
```

在 `peerimeter` 的 `setter` 中，新的值会被默认的定义为 `newValue`，你可以在 `set` 后使圆括号 `()` 来提供一个确定的名字

注意在 `EquilateralTriangle` 类初始化的时候执行了三个不同的步骤

- 设置子类中定义的属性值
- 调用父类的初始化方法
- 改变父类中属性的值。一些额外的设置工作（调用方法、取值、设置值）也可以在这执行，

如果你不需要去计算属性的值，但仍然需要在属性设置值的时候执行一些方法，使用 `willSet` 和 `didSet` 。你提供的代码会初始方法外任何属性值改变的时候被调用

```
class TriangleAndSquare {
	var triangle: EquilateralTriangle {
		willSet {
			square.sideLength = newValue.sideLength
		}
	}
	var square: Square {
		willSet {
			triangle.sideLength = newValue.sideLength
		}
	}
	init(size: Double, name: String) {
		square = Square(sideLength: size, name: name)
		triangle = EquilateralTriangle(sideLength: size, name: name)
	}
}
var triangleAndSquare = TriangleAndSquare(size: 10, name:"another test shape")
print(triangleAndSquare.square.sideLength) // 10
print(triangleAndSquare.triangle.sideLength) // 10
triangleAndSquare.square = Square(sideLength: 50, name:"Large square")
print(triangleAndSquare.triangle.sideLength) // 50
```

在使用可选值时，你可以在调用方法、读取属性、下标操作前使用 `?` 。如果 `?` 前的值为 `nil` ，在 `?` 后面的所有操作都会被忽略，并且整个表达式的值也会为 `nil`。
<del>否则，可选值会被拆箱，`?` 后面的所有东西都会遵从这个拆箱的值</del>。在这两种情况，整个表达式的值是一个可选类型

```
let optionalSquare: Square = Square(sideLength: 2.5, name: "opional square")
let sideLength = optionalSquare?.sideLength
```

使用 `enum` 创建一个枚举，<del>像类和所有其他的类型，枚举可以使用方法组合他们</del>

```
enum Rank: Int {
	case ace = 1
	case two, three, four, five, six, seven, eight, nine, ten
	case jack, queen, king
	func simpeDescription() -> String {
		switch self {
			case .ace:
				return "ace"
			case .jack:
				return "jack"
			case .queen:
				return "queen"
			case .king:
				return "king"
			default:
				return String(self.rawValue)
		}
	}
}
let ace = Rank.ace
let aceRawValue = ace.rawValue
```

默认情况下，Swift 从零开始给每行赋值，每次回自动增长，但是你也可以改变这个行为通过确切的表明它的值。上面的例子 `ace` 被明确的赋值为 1，接下来的值会被按顺序赋值。你也可以使用字符串或浮点数作为一个枚举每行的值类型。使用 `rawValue` 属性去读取枚举每行具体的值

使用 `init?(rawValue:)` 初始化一个枚举实例