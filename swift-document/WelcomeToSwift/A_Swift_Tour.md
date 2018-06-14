A Swift Tour
=======
[The Swift Programming Language - A Swift Tour](https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/GuidedTour.html)

전통적으로 처음 새로운 program language를 배울때, "Hello world"를 화면에 띄우는 것으로 시작하죠.<br>
Swift 에서는 한 줄로 이 것을 수행 가능합니다.

```swift
print("Hello world!")
```
C 혹은 Objective-C로 코드를 작성해본 경험이 있다면, 이 문법은 익숙하게 느껴질 것입니다.<br>
이 한줄의 코드는 완전한 프로그램입니다.<br>
입/출력 또는 문자열 처리를 위해 별도의 라이브러리를 import할 필요가 없습니다.<br>
전역(Global scope)으로 작성된 코드는 프로그램 진입 시점에 사용되기 때문에 main() function이 필요 없습니다.<br>
또한 모든 문장의 끝에 세미콜론을 사용할 필요 없습니다.<br>

이 문서에서는 다양한 programming task를 수행하는 방법을 보여줌으로써, Swift로 코드를 작성하기에 충분한 정보를 제공해줄 것입니다.<br>
이해하지 못해도 걱정 마세요. 이 문서에서 설명하는 모든 부분은 더 자세하게 각각의 가이드에서 충분한 설명을 할것입니다.<br>

> 최고의 학습 경험을 위한다면 Xcode의 Playground를 이용해 보세요. 코드를 편집하고, 즉시 결과를 확인할 수 있습니다.

Simple values
---
`let` : 상수 선언 <br>
`var` : 변수 선언

```swift
var myVariable = 42
myVariable = 50
let myConstant = 42
```

상수 또는 변수는 할당하려는 값과 같은 타입이어야 합니다. 하지만 항상 명시적으로 type을 적어주지 않아도 됩니다. <br>
상수 또는 변수를 만들때 값을 할당하면 컴파일러는 type을 추론합니다. <br>
위 예제에서 컴파일러는 초기 할당값이 integer이기 때문에 myVariable이 integer임을 유추합니다.<br>
초기값이 type 추론을 위해 충분한 값을 제공하지 못하거나, 초기값이 없는 경우에는 변수뒤에 콜론(:)을 구분하여 유형을 지정하십시오<br>
```swift
let explicitDouble: Double = 70
```
값은 암묵적으로 다른 타입으로 변경되지 않습니다. 만약 다른 타입으로의 변환이 필요하다면, 명시적으로 원하는 타입의 instance로 만들어 주십시오
```swift
let label = "The width is "
let width = 94
let widthLabel = label + String(width)
```

String 안에 값을 넣는 간단한 방법을 제공합니다.<br>
괄호 안에 값을 넣고, backslash(\\)를 괄호 앞에 써주세요 <br>
```swift
let apples = 3
let oranges = 5
let appleSummary = "I have \(apples) apples."
let fruitSummary = "I have \(apples + oranges) pieces of fruit."
```

Array나 Dictionary를 선언할 때는 brackets([])를 사용하세요. 그리고 index 혹은 key를 통해 elements에 접근하세요.<br>
마지막 element 뒤에도 Comma(,)를 넣을 수 있습니다.
```swift
var shoppingList = ["catfish", "water", "tulips", "blue paint"]
shoppingList[1] = "bottle of water"
 
var occupations = [
    "Malcolm": "Captain",
    "Kaylee": "Mechanic",
]
occupations["Jayne"] = "Public Relations"
```

빈 Array나 Dictionary를 만들고 싶으면 초기화 구문을 사용하세요
```swift
let emptyArray = [String]()
let emptyDictionary = [String: Float]()
```

타입이 추론 가능한 경우에는 [] (Array), [:] (Dictionary) 이렇게 초기화도 가능합니다<br>
(선언된 변수에 초기값을 할당하는 경우나, 함수의 인자로 넘기는 경우)
```swift
shoppingList = []
occupations = [:]
```

Control flow
----
`if` 나 `swifth` 로 조건문을 사용하세요. `for-in`, `while`, `repeat-while` 로 loop를 사용하세요<br>
`if` 안에는 Boolean expression만 사용 가능합니다.<br>
`if`와 `let`을 함께 사용해서 missing value를 처리할 수 있습니다. (Optional value)<br>
Optional value는 값을 갖고 있거나 혹은 nil (missing value) 상태를 포함합니다.<br>
물음표(?)를 값 뒤에 붙여서 optional value임을 표시합니다.
```swift
var optionalString: String? = "Hello"
print(optionalString == nil)
 
var optionalName: String? = "John Appleseed"
var greeting = "Hello!"
if let name = optionalName {
    greeting = "Hello, \(name)"
}
```

위 예제에서 optional value가 nil이면 조건부가 false가 되어 중괄호 내 코드를 건너뜁니다.<br>
반대로 let 으로 선언된 상수에 할당이 된다면, unwrapped 상태인 optional 값이 블록 내에서 사용 가능하도록 됩니다.<br>
<br>
Optional 값을 처리하는 또다른 방법은 `??` 연산자를 사용하는 것입니다. Optional value가 nil 이라면 default 값을 대신 사용할 수 있도록 합니다.
```swift
let nickName: String? = nil
let fullName: String = "John Appleseed"
let informalGreeting = "Hi \(nickName ?? fullName)"
```
Switch 문은 모든 종류의 데이터와 다양한 비교연산을 지원합니다.<br>
integer나 동등비교 연산만이 아닙니다
```swift
let vegetable = "red pepper"
switch vegetable {
case "celery":
    print("Add some raisins and make ants on a log.")
case "cucumber", "watercress":
    print("That would make a good tea sandwich.")
case let x where x.hasSuffix("pepper"):
    print("Is it a spicy \(x)?")
default:
    print("Everything tastes good in soup.")
}
```
패턴에 맞는 값을 `let` 을 통해서 상수에 할당하는 부분을 주목하세요<br>
<br>
일치하는 case 구문을 수행하고, switch문을 빠져나갑니다. 다음 케이스까지 수행하지 않기 때문에 break를 써줄 필요는 없습니다<br>
<br>
`for-in` 을 통해 key-value pair로 Dictionary 를 순회할 수 있습니다.<br>
Dictionary는 unordered collection이기 때문에 key-value는 임의의 순서로 순회 가능합니다.<br>
<br>
`while`을 사용하면 조건에 벗어날때까지 코드블록을 반복할 수 있습니다. `repeat-while`을 통해 조건을 끝에 두면, 적어도 한번 수행되도록 할 수 있습니다.
```swift
var n = 2
while n < 100 {
    n *= 2
}
print(n)
 
var m = 2
repeat {
    m *= 2
} while m < 100
```
..< 를 사용하여 range를 만들 수 있습니다.<br>
..< : 미만, ... : 이하
```swift
var total = 0
for i in 0..<4 {
    total += i
}
print(total)
```

Function and closures
---
`func` 를 사용하여 함수를 선언합니다. -> 구분자로 파라미터/함수이름 과 리턴타입을 구분합니다.<br>

```swift
func greet(person: String, day: String) -> String {
    return "Hello \(person), today is \(day)."
}
greet(person: "Bob", day: "Tuesday")
```
기본적으로 함수는 parameter의 이름을 argument 레이블로 사용합니다. 아래처럼 custom argument label을 쓸 수 있고, 혹은 인수 없는 레이블 _ 을 쓰세요
```swift
func greet(_ person: String, on day: String) -> String {
    return "Hello \(person), today is \(day)."
}
greet("John", on: "Wednesday")
```
튜플을 사용하면, 값을 묶을 수 있습니다. 예를 들어 여러개의 값을 리턴하는 함수라고 합시다. 튜플의 엘리먼트는 이름이나 숫자로 참조 가능합니다.
```swift
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
let statistics = calculateStatistics(scores: [5, 3, 100, 3, 9])
print(statistics.sum)
print(statistics.2)
```

함수는 중첩 가능합니다. 내부에 선언된 함수는 외부 함수의 변수에 접근 가능합니다.
```swift
func returnFifteen() -> Int {
    var y = 10
    func add() {
        y += 5
    }
    add()
    return y
}
returnFifteen()
```
함수는 일급 객체(first-class type) 입니다. 이는 함수가 함수를 값으로 리턴할 수 있다는 뜻입니다.
```swift
func makeIncrementer() -> ((Int) -> Int) {
    func addOne(number: Int) -> Int {
        return 1 + number
    }
    return addOne
}
var increment = makeIncrementer()
increment(7)
```
또한 parameter로 함수를 받을 수 있습니다.
```swift
func hasAnyMatches(list: [Int], condition: (Int) -> Bool) -> Bool {
    for item in list {
        if condition(item) {
            return true
        }
    }
    return false
}
func lessThanTen(number: Int) -> Bool {
    return number < 10
}
var numbers = [20, 19, 7, 12]
hasAnyMatches(list: numbers, condition: lessThanTen)
```

함수는 실제로 closure의 특별한 케이스입니다. closure는 향후에 호출이 가능한 코드블록입니다.<br>
closure 는 closure가 생성될 당시의 scope에서 사용 가능 범위에 있던 변수나 함수들에 엑세스 할 수 있습니다. <br>
심지어 클로저가 실제로 실행될 때 다른 scope에 있더라도 말입니다. (중첩 함수로 예시에서 이를 알 수 있습니다)<br>
중괄호 ({}) 로 둘러싼 코드로 이름없는 closure를 만들 수 있습니다. argument와 return type은 `in` 을 사용하여 body와 구분합니다.
```swift
numbers.map({ (number: Int) -> Int in
    let result = 3 * number
    return result
})
```

closure 를 간결하게 작성하도록 하는 몇가지 옵션이 있습니다. closure의 type을 이미 알고 있는 경우입니다. (delegate의 callback 등)<br>
parameter의 type, return type 을 생략 가능합니다.<br>
closure 내의 한줄짜리 명령은 암묵적으로 return 구문으로 사용됩니다.
```swift
let mappedNumbers = numbers.map({ number in 3 * number }) // return 3*number
print(mappedNumbers)
```

parameter의 이름 대신 숫자로 참조할 수 있습니다. 이는 짧은 closure를 만들때 유용합니다.<br>
또한 함수의 마지막 argument로 전달될 closure는 괄호 바로 뒤에 사용할 수 있습니다.
```swift
test(10, 20){ $0 > $1 }
```
closure가 함수의 유일한 parameter라면 함수 호출시 괄호를 생략 가능합니다.
```swift
let sortedNumbers = numbers.sorted { $0 > $1 }
print(sortedNumbers)
```

Objects and Classes
---

`class` 를 사용하여 클래스를 만드세요. 클래스 내 속성 선언은 클래스의 context 내에 선언한다는 것 빼고는 상수나 변수를 선언했던 방식과 동일합니다.<br>
물론 함수도 마찬가지 입니다.

```swift
class Shape {
    var numberOfSides = 0
    func simpleDescription() -> String {
        return "A shape with \(numberOfSides) sides."
    }
}
```
클래스 이름 뒤에 괄호를 넣어 instance를 만들고, "." 구문을 사용하여 속성 및 함수에 엑세스 합니다.

```swift
var shape = Shape()
shape.numberOfSides = 7
var shapeDescription = shape.simpleDescription()
```
```swift
`init` 함수를 사용해서 인스턴스 생성시 클래스의 initializer를 만드세요
class NamedShape {
    var numberOfSides: Int = 0
    var name: String
    
    init(name: String) {
        self.name = name
    }
    
    func simpleDescription() -> String {
        return "A shape with \(numberOfSides) sides."
    }
}
```

`self` 를 사용하여 클래스 내의 name 과 argument 인 name를 구분하는것에 주목하세요<br>
모든 속성들은 값이 할당이 되어야 합니다.(선언시, 혹은 intializer 안에서)<br>
instance 생성시 initializer에 argument들을 함수 호출하듯 넘겨주세요<br>
<br>
`deinit`으로 deinitializer를 만들 수 있습니다. 객체가 deallocated 되기 전에 cleanup을 해야 한다면 활용하세요.<br>
<br>
상속은 super class의 이름과 콜론(:)을 클래스 이름 뒤에 붙이면 됩니다.<br>
<br>
super class의 함수를 오버라이드 하는 경우 `override` 를 앞에 붙입니다. 모르고 우연히 오버라이드 하는 경우, 컴파일러가 오류를 뱉습니다.<br>
```swift
class Square: NamedShape {
    var sideLength: Double
    
    init(sideLength: Double, name: String) {
        self.sideLength = sideLength
        super.init(name: name)
        numberOfSides = 4
    }
    
    func area() -> Double {
        return sideLength * sideLength
    }
    
    override func simpleDescription() -> String {
        return "A square with sides of length \(sideLength)."
    }
}
let test = Square(sideLength: 5.2, name: "my test square")
test.area()
test.simpleDescription()
```
속성의 경우, 값을 단순히 저장하는것 외에 getter, setter를 가질 수 있습니다.
```swift
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
        return "An equilateral triangle with sides of length \(sideLength)."
    }
}
var triangle = EquilateralTriangle(sideLength: 3.1, name: "a triangle")
print(triangle.perimeter)
triangle.perimeter = 9.9
print(triangle.sideLength)
```

setter 내에서 암묵적으로 새 값은 `newValue`로 사용됩니다. 물론 이름을 명시할 수 있습니다<br>
<br>

get, set 내에서 처럼 속성에 대한 계산을 할 필요는 없지만, 무언가 값을 세팅하기 전,후에 실행해야 할 코드가 있다면 `willSet`, `didSet` 을 사용하세요.<br>
initializer 외부에서의 값 변경 시 마다 해당 코드는 실행될 겁니다.<br>
예를 들어, 아래 예시에서는 삼각형의 한 변의 길이가 네모의 변의 길이와 같도록 합니다.
```swift
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
var triangleAndSquare = TriangleAndSquare(size: 10, name: "another test shape")
print(triangleAndSquare.square.sideLength)
print(triangleAndSquare.triangle.sideLength)
triangleAndSquare.square = Square(sideLength: 50, name: "larger square")
print(triangleAndSquare.triangle.sideLength)
```

optional value를 사용할 때. `?` 를 함수나 속성, subscripting을 사용하기 전에 붙여주세요.<br>
만약 `?` 전의 값이 `nil` 이라면 `?` 뒤에 모든 구문은 `nil` 이 됩니다.
```swift
let optionalSquare: Square? = Square(sideLength: 2.5, name: "optional square")
let sideLength = optionalSquare?.sideLength
```

Enumerations and Structures
---
`enum` 으로 enumeration 을 사용하세요. enum 안에는 함수도 선언 가능합니다.
```swift
enum Rank: Int {
    case ace = 1
    case two, three, four, five, six, seven, eight, nine, ten
    case jack, queen, king
    func simpleDescription() -> String {
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
기본적으로 Swift에서는 0에서 시작하여 1씩 증가하는 raw value를 할당합니다. 물론 명시적으로 값을 지정하여 이 규칙을 바꿀 수 있습니다.<br>
위의 예에서 Ace에 명시적으로 1 이라는 raw value를 할당해 주었기 때문에, 나머지 raw value들은 그 뒤로 순차적으로 지정됩니다.<br>
또한 raw value로 부동소수 숫자도 할당 가능합니다.<br>
`rawValue` 속성으로 enumeration 의 raw value를 사용할 수 있습니다.<br>
<br>
`init?(rawValue:)` 함수를 사용하면 raw value로 enumeration의 instance를 생성할 수 있습니다.<br>
이는 raw value와 매치되는 enumeration 객체를 리턴하거나, 매치되는 경우가 없다면 `nil`을 반환합니다.

```swift
if let convertedRank = Rank(rawValue: 3) {
    let threeDescription = convertedRank.simpleDescription()
}
```

enumeration의 case 값들은 실제 존재하는 값이 되는 것이지, raw value를 활용하기 위한 다른 방안 같은건 아닙니다.<br>
의미있는 raw value를 제공할 필요가 없는 상황이라면 굳이 raw value는 쓰지 않아도 됩니다.
```swift
enum Suit {
    case spades, hearts, diamonds, clubs
    func simpleDescription() -> String {
        switch self {
        case .spades:
            return "spades"
        case .hearts:
            return "hearts"
        case .diamonds:
            return "diamonds"
        case .clubs:
            return "clubs"
        }
    }
}
let hearts = Suit.hearts
let heartsDescription = hearts.simpleDescription()
```

위 예제에서 enumeration의 case 중 하나인 `hearts`를 사용하는 2가지 방법에 주목하세요<br>
상수(`let hearts`)에 할당하려 할 때, `Suit.hearts` 이렇게 전체 이름을 사용하는데, 상수에 명시적 유형이 지정되지 않기 때문입니다.<br>
반면에 switch 내부에서는 축약된 형태인 `.hearts`로 사용하는데요, 왜냐면 `self`의 type은 이미 알고 있기 때문이죠<br>
타입이 추론 가능하다면, 언제든 축약된 형태로 사용 가능합니다.<br>
<br>
enumeration이 raw value를 가지고 있다면, 같은 case의 모든 enumeration instance는 같은 raw value를 가지고 있을 것 입니다.<br>
또 다른 enumeration case의 선택 사항은 instance를 만들 때 연관된 값(Associated value)을 갖도록 하여, <br>
instance마다 다른 연관된 값을 갖도록 하는 것입니다.<br>
마치 stored properties라고 생각하면 됩니다.<br>
서버에서 일출과 일몰 시간을 요청하는 경우가 있다고 생각해 보십쇼.<br>
서버는 요청된 정보에 맞게 response 를 주거나, 에러를 뱉을 겁니다<br>
```swift
enum ServerResponse {
    case result(String, String)
    case failure(String)
}
 
let success = ServerResponse.result("6:00 am", "8:09 pm")
let failure = ServerResponse.failure("Out of cheese.")
 
switch success {
case let .result(sunrise, sunset):
    print("Sunrise is at \(sunrise) and sunset is at \(sunset).")
case let .failure(message):
    print("Failure...  \(message)")
}
```

switch cases 와 값을 비교할때 일출, 일몰 시간이 ServerResponse에서 어떻게 추출되는지 주목합시오.<br>
<br>

`struct` 를 사용하여 구조체를 만드세요. 구조체는 메소드, 초기화구문 등 클래스와 동일한 많은 동작들을 지원합니다.<br>
구조체와 클래스의 가장 중요한 차이점 중 하나는, 구조체는 항상 값을 전달할 때 copy를 한다는 것 입니다. 클래스는 주소를 전달하죠.

```swift
struct Card {
    var rank: Rank
    var suit: Suit
    func simpleDescription() -> String {
        return "The \(rank.simpleDescription()) of \(suit.simpleDescription())"
    }
}
let threeOfSpades = Card(rank: .three, suit: .spades)
let threeOfSpadesDescription = threeOfSpades.simpleDescription()
```

Protocols and Extensions
---
`protocol`을 사용하여 프로토콜을 만드세요
```swift
protocol ExampleProtocol {
    var simpleDescription: String { get }
    mutating func adjust()
}
```
클래스, 열거형, 구조체는 프토토콜의 구현체가 될 수 있습니다.
```swift
class SimpleClass: ExampleProtocol {
    var simpleDescription: String = "A very simple class."
    var anotherProperty: Int = 69105
    func adjust() {
        simpleDescription += "  Now 100% adjusted."
    }
}
var a = SimpleClass()
a.adjust()
let aDescription = a.simpleDescription
 
struct SimpleStructure: ExampleProtocol {
    var simpleDescription: String = "A simple structure"
    mutating func adjust() {
        simpleDescription += " (adjusted)"
    }
}
var b = SimpleStructure()
b.adjust()
let bDescription = b.simpleDescription
```

구조체를 수정하려고 할 때 `mutating` 키워드가 붙은 함수를 사용하는 것에 대해 주목하세요.<br>
클래스의 경우에는 항상 클래스의 메소드가 클래스를 수정할 수 있기 때문에 붙이지 않습니다.<br>
<br>
`extension`을 사용하여 새 함수 및 계산속성(computed-properties)를 추가할 수 있습니다.<br>
라이브러리, 프레임워크의 클래스, 열거형, 구조체에도 `extension`을 통해 프로토콜을 구현하도록 할 수 있습니다.

```swift
extension Int: ExampleProtocol {
    var simpleDescription: String {
        return "The number \(self)"
    }
    mutating func adjust() {
        self += 42
    }
}
print(7.simpleDescription)
```

다른 타입의 object지만 하나의 protocol을 따르도록 하여 collection에서 하나의 type으로 관리하는 등 하나의 type들처럼 사용할 수 있습니다<br>
하지만 그럴때는 protocol에서 선언된 공통 타입에만 접근이 가능할 것 입니다.
```swift
let protocolValue: ExampleProtocol = a
print(protocolValue.simpleDescription)
// print(protocolValue.anotherProperty)  // Uncomment to see the error
```

심지어 `protocolValue`가 runtime 시 type이 SimpleClass라고 하더라도, 컴파일러는 `ExampleProtocol`라는 주어진 타입으로 취급합니다.<br>
즉, 위 케이스에선 protocol에 준수한 속성과 메소드가 아니면 사용할 수 없습니다.

Error Handling
---

`Error` 프로토콜을 따르는 모든 유형을 활용해서 에러를 다룰 수 있습니다.
```swift
enum PrinterError: Error {
    case outOfPaper
    case noToner
    case onFire
}
```

`throw`를 사용하여 오류를 발생시키고, `throws` 를 사용하여 오류가 발생 가능한 함수라는것을 표시합니다.

```swift
func send(job: Int, toPrinter printerName: String) throws -> String {
    if printerName == "Never Has Toner" {
        throw PrinterError.noToner
    }
    return "Job sent"
}
```
몇가지 에러를 핸들링 할 수 있는 방법이 있습니다. 먼저 `do-catch`. `do` 블록 안에서 오류가 반환될 수 있는 코드 앞에 `try`를 표시합니다.<br>
`catch` 블록에 별다른 오류 이름을 지정하지 않으면 `error`라는 이름으로 오류 객체를 사용합니다.

```swift
do {
    let printerResponse = try send(job: 1040, toPrinter: "Bi Sheng")
    print(printerResponse)
} catch {
    print(error)
}
```
여러개의 `catch`블록을 사용할 수 있습니다. switch를 사용하는 것 처럼 catch 뒤에 패턴을 작성합니다.
```swift
do {
    let printerResponse = try send(job: 1440, toPrinter: "Gutenberg")
    print(printerResponse)
} catch PrinterError.onFire {
    print("I'll just put this over here, with the rest of the fire.")
} catch let printerError as PrinterError {
    print("Printer error: \(printerError).")
} catch {
    print(error)
}
```
또 다른 방법은, `try?` 를 사용하는 것 입니다. 함수가 에러를 던지면 오류는 무시되고 nil이 반환됩니다.<br>
그렇지 않다면, 함수의 리턴값이 반환됩니다.
```swift
let printerSuccess = try? send(job: 1884, toPrinter: "Mergenthaler")
let printerFailure = try? send(job: 1885, toPrinter: "Never Has Toner")
```

`defer` 를  사용해서 함수의 모든 코드가 실행되고 나서 (return 전에) 실행될 코드블록을 작성하세요.<br>
함수가 오류를 throw하는지 관계없이 실행됩니다.<br>
`defer`를 통해 setup 코드와 cleanup 코드를 붙여서 써놓을 수 있습니다. 비록 그들이 다른 타이밍에 수행되더라두요<br>
```swift
var fridgeIsOpen = false
let fridgeContent = ["milk", "eggs", "leftovers"]
 
func fridgeContains(_ food: String) -> Bool {
    fridgeIsOpen = true
    defer {
        fridgeIsOpen = false
    }
    
    let result = fridgeContent.contains(food)
    return result
}
fridgeContains("banana")
print(fridgeIsOpen)
```

Generics
---

Generic 타입의 함수나 type을 만드려면 <> 안에 이름을 쓰면 됩니다.
```swift
func makeArray<Item>(repeating item: Item, numberOfTimes: Int) -> [Item] {
    var result = [Item]()
    for _ in 0..<numberOfTimes {
        result.append(item)
    }
    return result
}
makeArray(repeating: "knock", numberOfTimes: 4)
```

함수, type 선언(클래스, 열거형, 구조체) 등에 generic form을 사용할 수 있습니다.<br>
<br>
아래 예시처럼 body 앞에 `where`를 사용하여 요구사항 목록을 지정하면,<br>
특정 프로토콜을 따르기를 바라거나, 두가지 type이 동일한 프로토콜을 따르거나 등의 요구사항을 명시할 수 있습니다
```swift
func anyCommonElements<T: Sequence, U: Sequence>(_ lhs: T, _ rhs: U) -> Bool
    where T.Iterator.Element: Equatable, T.Iterator.Element == U.Iterator.Element {
        for lhsItem in lhs {
            for rhsItem in rhs {
                if lhsItem == rhsItem {
                    return true
                }
            }
        }
        return false
}
anyCommonElements([1, 2, 3], [3])
```

`<T: Equatable>` 과 `<T> ... where T: Equatable` 는 같은표현입니다.
