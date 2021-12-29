# ⛏ SwiftyBuilder

[![Version](https://img.shields.io/cocoapods/v/SwiftyBuilder.svg?style=flat)](https://cocoapods.org/pods/SwiftyBuilder)
[![License](https://img.shields.io/cocoapods/l/SwiftyBuilder.svg?style=flat)](https://cocoapods.org/pods/SwiftyBuilder)
[![Platform](https://img.shields.io/cocoapods/p/SwiftyBuilder.svg?style=flat)](https://cocoapods.org/pods/SwiftyBuilder)

## 🔧 Installation

SwiftyBuilder is available through [CocoaPods](https://cocoapods.org). To install
it, simply add the following line to your Podfile:

```ruby
pod 'SwiftyBuilder'
```

## 🤷‍♂️ What is Builder Pattern

https://github.com/kingreza/Swift-Builder

## 🤔 How to use

### Basic

- before

```swift
let view: UIView = {
    var view = UIView()
    view.backgroundColor = .black
    view.alpha = .zero
    return view
}()
```

- after

```swift
let view = UIView()
    .builder
    .backgroundColor(.black)
    .alpha(.zero)
    .build()
```

### Freely set properties

- the value types

```swift
let array = [""]
    .builder
    .do {
        $0.append("Hello")
    }
    .build()
```

- `NSObject` subclasses

```swift
let button = UIButton()
    .builder
    .apply {
        $0.setTitle("Hello, World", for: .normal)
    }
    .build()
```

### Custom Builder

- declare

```swift
struct User: Buildable {
    var id: String?
    var name: String?
}
```

```swift
typealias UserBuilder = Builder<User>
// or
extension Builder where Base == User {}
```

- intercept

```swift
extension UserBuilder {
    func id(_ value: String) -> Self {
        return set(\.id, value: "ID : \(value)")
    }
}
```

```swift
let user = User()
    .builder
    .id("user")
    .build()
    
print(user.id!) // ID : user 
```

## 👀 References

https://github.com/devxoul/Then

## License

SwiftyBuilder is available under the MIT license. See the LICENSE file for more info.
