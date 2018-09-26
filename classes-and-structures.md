#### 相同点

* 定义属性用来存储值。
* 定义方法提供功能。
* 定义下标脚本用来允许下标语法访问值。
* 定义初始化器来初始化状态。
* 可被扩展默认没有的功能。
* 遵守协议来针对特定类型提供标准功能。

#### 类的其他功能

* 类允许一个类继承另一个类的特征。
* 类型转换 允许你在 运行检查和解释 一个类实例 的类型。??
* 反初始化器允许你在一个类实例释放任何被其所分配的资源。
* 引用计数允许类有不止一个引用。

#### 定义

```swift
class SomeClass {

}

struct SomeStructure {

}

struct Resolution {
    var width = 0
    var height = 0
}

class VideoMode {
    var resolution = Resolution()
    var interlaced = false
    var frameRate = 0.0
    var name: String?
}
```

#### 实例

```swift
let someResolution = Resolution()
let someVideoMode = VideoMode()
```

#### 访问属性

```swift
print("width: \(someResolution.width)") // width: 0

print("height: \(someVideoMode.resolution.height)") // height: 0

someVideoMode.resolution.width = 1080
print("width: \(someVideoMode.resolution.width)") // width: 1080
```

* 与 Objective-C 不同，Swift 的结构体允许直接一个结构体属性的子属性。

#### 结构体的成员初始化器

* 结构体会自动生成一个默认的 **成员初始化器**。
* 新实例的属性会通过属性名传递到成员初始化器中。

```swift
let vga = Resolution(width: 640, height: 480)
```

* 类实例不会接收默认的成员初始化器。

#### 结构体值类型

* 当被赋值给常量、变量，传递给函数的时候，会被**拷贝**一份。

```swift
let hd = Resolution(width: 1920, height:1080)
var cinema = hd
cinema.width = 2048
print("hd width: \(hd.width)") // hd width: 1820
print("cinema width: \(cinema.width)") // cinema width: 2048
// cinema 的值改变不会影响 hd
```

#### 类引用类型

* 当被赋值给常量、变量，传递给函数的时候，不会发生拷贝，而是对当前实例的一个**引用**。

```swift
let tenEighty = VideoMode()
tenEighty.resolution = hd
tenEighty.interlaced = true
tenEighty.name = '1080i'
tenEighty.frameRate = 25.0
```

声明了一个新的名叫 `tenEighty` 的常量并且设置它引用了一个 \`VideoMode\` 类的新实例，这个视频复制了之前的 1920 x 1080的 HD 分辨率，同时设置为隔行扫描，并给予了一个名字 1080i，设置了 25.0 帧每秒的频率。

