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

* 使用 `+` 运算符来连接两个字符串

```
let str1 = "pick"
let str2 = "haha"
var newStr = str1 + str2  // pickhaha
```

* 使用 `+=` 运算符在现有字符串后追加字符串

```
var str = "pick"
str += "haha"  // pickhaha
```

#### 



