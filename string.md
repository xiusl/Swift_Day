# One

#### 字面量

```
let name = "swift day"
```

#### 多行

```
let letter = """
Fools learn nothing from wise men, 
but wise men learn much from fools.
"""
```

#### 空串

```
var emptyString = ""
var emptyString2 = String()

if emptyString.isEmpty {
    print("is empty")
}
```

#### 可变性

* 与 Objective-C 不同，Swift使用 `var` 声明变量来表示可变的，`let` 声明常量来表示不可变。

#### 值类型

* `String` 在赋值给常量、变量，传递给方法、函数的时候会拷贝一份。
* Swift 只有的需要的时候才会进行拷贝，提高了性能。

#### 字符

* 使用 `Character` 来创建一个单字符的变量或常量。

```
let aChar: Character = "a"
```

* `String` 可以根据 `Character` 数组来作为初始化参数。

```
let chars: [Character] = ["H", "e", "l", "l", "o", "!"]
let sayHi = String(chars)
```

* 拼接字符，`String` 相当于一个 `Character` 数组，使用数组的方法拼接字符。

```
var aStr = "the"
aStr.append(aChar) // thea
```

#### 拼接

* 使用 `+` 运算符来连接两个字符串。

```
let str1 = "pick"
let str2 = "haha"
var newStr = str1 + str2  // pickhaha
```

* 使用 `+=` 运算符在现有字符串后追加字符串。

```
var str = "pick"
str += "haha"  // pickhaha
```

#### 字符串插值

* 混合常量、变量、字面值和表达式字符串构造新的字符串。
* 插入的值使用 `()` 包裹，以 `\` 作为前缀。

```
let multiplier = 3
let message = "\(multiplier) times 2.5 is \(Double(multiplier) * 2.5)"
// 3 times 2.5 is 7.5
```

#### Unicode

* 一种在不同书写系统中编码、表示和处理文本的统一标准。
* Swift 中的`String` 和 `Character` 是完全 Unicode 兼容的。
* Unicode 标量。???

#### 特殊字符

* 转义字符  `\` 。

```
\0 空字符，\\ 反斜杠，\t 水平制表符，\n 换行符，\r 回车，\" 双引号，\' 单引号
```

* `Unicode` 标量， `\u{n}`~~ n是一个  1-8 个与合法 Unicode 码位相等的 16 进制数字~~。??

```
let dollar = "\u{24}"   // $，U+0024
let heart = "\u{2665}"  // ❤，U+2665
let sparkling = "\u{1F496}"  // ?，U+1F496
```

#### 拓展字形

* ???

#### 字符统计

* 获取字符串长度，`String` 中 `Character` 的个数，`String` 的 `count` 属性。

```
let unusualManagerie = "Koala?, Snail?,"
print("unusualManagerie has \(unusualManagerie.count) characters.")
```

#### 字符串索引



