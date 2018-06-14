The Basics
====
[The Swift Programming Language - The Basics](https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/TheBasics.html)

Swift는 iOS, macOS, watchOS 및 tvOS 앱 개발을 위한 새로운 프로그래밍 언어입니다.<br>
그렇지만 Swift 의 많은 부분은 C/Objective-C를 개발했던 당신의 경험으로 보았을때 친숙하게 느껴질 것 입니다.<br>
<br>
Swift 는 C/Objective-C의 기본 타입들 (Int, integer, Double, Float, Bool, String)을 제공합니다.<br>
또한 Swift는 파워풀한 세가지 기본 유형의 켈렉션 타입 또한 제공합니다. Array, Set, Dictionary<br>
(이는 "[Collection type]()" 편에서 자세히 설명합니다)<br>
<br>
C 와 마찬가지로 Swift는 변수를 통해 값을 저장하고, 그 값에 식별할 수 있는 이름을 부여하여 참조하도록 합니다.<br>
또한 Swift는 광범위하게 사용될, 값을 바꿀 수 없는 변수도 제공을 하는데요. 이는 "상수(Constant)"라고 하죠.<br>
Swift 의 상수는 C보다 훨씬 강력합니다.<br>
Swift에서의 상수를 통해 변경할 필요가 없는 값들을 다루게 되면, 코드를 안전하고 명확하게 만들 수 있습니다.<br>
<br>
이처럼 익숙한 유형들 외에도 Swift에선 Tuple과 같은 Objective-C에서도 없었던 고급 유형들을 제공합니다<br>
Tuple을 사용하면 값들을 그룹지어 생성하고 전달할 수 있습니다. Tuple을 통해 여러개의 값을 함수에서 묶어서 return할 수 있습니다<br>
<br>
Swift는 또한 "Optional" type을 제공합니다. 이는 없는(absence, nil)값을 다루도록 도와줍니다.<br>
Optional은 "값이 있어! 그 값은 x야" 혹은 "값이 없어..." 둘 다를 의미합니다<br>
Optional을 사용하는 것은 Objective-C에서 pointer변수의 nil이 있는 사용 패턴과 비슷하지만, 클래스 뿐만이 아닌 모든 타입에서 제공됩니다.<br>
Objective-C의 nil pointer보다 안전하고, 표현력이 뛰어나며, Swift의 가장 강력한 기능 중 하나입니다.<br>
<br>
Swift는 type-safe 언어입니다. 이는 언어 차원에서 당신이 코드에서 사용하는 값의 타입에 대해 명확하게 작성하도록 도와줍니다.<br>
String을 필요로 한다면, type-safe는 실수로라도 Int를 전달하지 못하도록 막습니다.<br>
또한 non-optional 인 String에 optional인 String을 전달하는 경우도 막습니다.<br>
Type-safe는 개발 단계에서 가능한 빨리 오류를 포착하고 수정하도록 도와줍니다.
<br>

Constants and Variables (상수와 변수)
--- 
상수 그리고 변수는 이름과 여러 타입의 값을 갖습니다. "상수"는 한번 설정되면 변경할 수 없으며, 변수는 미래에 언젠가 변경될 수 있음을 뜻합니다<br>

### 선언하기
상수와 변수는 그들이 사용되기 전에 선언되어야 합니다. 상수는 `let` 키워드로 선언하고, 변수는 `var`키워드로 선언한다<br>
한 줄에 여러개의 상수 또는 변수를 쉼표로 구분하여 선언할 수 있다
```swift
var x = 0.0, y = 0.0, z = 0.0
```

### Type Annotations (타입 설명, 주석)
상수와 변수를 선언할 때, 이 변수나 상수가 어떤 type의 값을 저장할지 명확하게 하기 위해 type annotation을 제공할 수 있다.
변수와 상수 이름 이후에 콜론(:) 뒤에, 그 뒤에 공백이 오고, 타입 명을 적어주면 된다.<br>
다음 예시는 `welcomeMessage`변수에 String 타입의 값을 저장할 수 있다고 가리키는 type annotation을 제공한 예시이다.
```swift
var welcomeMessage: String
``
이때의 콜론(:)의 의미는 "...의 타입은.."이다. 따라서 위 예시는 다음처럼 해석하면 된다<br>
"`welcomeMessage`라는 이름을 가진 선언된 변수의 type은 String 이야"<br>
<br>
한 줄에 여러개의 같은 타입을 가지는 변수들을 선언할 수 있다.
```swift
var red, green, blue: Double
```

### Naming Constants and Variables
상수와 변수의 이름에는 거의 모든 문자를 쓸 수 있다 (유니코드 포함)
```swift
let π = 3.14159
let 你好 = "你好世界"
let 🐶🐮 = "dogcow"
```
상수와 변수 이름에는 공백, 수학기호, 화살표, [private-use Unicode](https://en.wikipedia.org/wiki/Private_Use_Areas), [선, Box 그리기 문자](https://en.wikipedia.org/wiki/Box-drawing_character) 를 사용할 수 없습니다.<br>
숫자로 시작할 수 없으며, 숫자는 이름 내에 포함될 순 있습니다.<br>
<br>
특정 타입을 갖는 변수 혹은 상수를 선언 한 뒤에, 같은 이름의 변수 혹은 상수를 타입을 변경하는 것은 불가능합니다. 상수와 변수간의 변경도 불가능합니다.<br>
변수의 경우 같은 타입의 다른 값으로 변경이 가능하지만, 상수의 경우에는 변경하려 하면 컴파일 시 오류를 뱉습니다<br>

### Printing Constants and Variables
`print(_:separator:terminator:)` 함수를 이용해 변수, 상수의 값을 출력할 수 있습니다.<br>
하나 이상의 값을 적절히 출력해주는 전역 함수입니다. Xcode에서는 "console" 패널에 출력을 해주죠. <br>
`separator`와 `terminator`는 기본값을 갖고 있습니다. (따라서 생략 가능)<br>
기본적으로 이 함수는 줄바꿈과 함께 출력을 수행합니다. 줄바꿈 없이 수행하고 싶다면 `terminator` 에 빈 문자열을 넘겨주면 됩니다.<br>
예를 들면 `print(someValue, terminator: "")` 이렇게요. 함수 기본값에 대한 내용은 나중에 "[Function]()"편에서 배웁니다.<br>
<br>
Swift 에서는 문자열 보간(String interpolation)을 사용하여 문자열 내 변수/상수 이름을 값으로 바꿔줍니다.<br>
괄호 () 와 backslash(\\)를 통해서 다음과 같이 사용합니다
```swift
print("The current value of friendlyWelcome is \(friendlyWelcome)")
```

Comments (주석)
---
.

Semicolons (세미콜론)
---
.

Integers
---
integer(정수)는 분수가 아닌 모든 숫자입니다. (ex : 42, -23). *signed* (+,0,-) 와 *unsigned* (+,0) 둘다 지원합니다.<br>
8, 16, 32, 64bit 의 integer를 지원합니다. 이것들은 C와 비슷한 명명 규칙(naming convention)을 따릅니다<br>
8-bit unsigned integer : `UInt8`, 32-bit signed integer `Int32`<br>
Swift의 다른 타입들과 마찬가지로, 대문자로 시작합니다.

### Integer bounds

min, max 속성을 사용해 각 정수 유형의 최대값, 최소값을 알 수 있습니다.
```swift
let minValue = UInt8.min  // minValue is equal to 0, and is of type UInt8
let maxValue = UInt8.max  // maxValue is equal to 255, and is of type UInt8
```
### Int

대부분의 케이스에서는, 굳이 integer의 bit size를 고민할 필요가 없습니다. Swift에선 `Int`타입을 지원하고, <br>
이는 현재 플랫폼의 기본 bit size와 동일합니다. 32-bit 플랫폼에서는 `Int` 와 `Int32`가 같고, 64-bit 플랫폼에서는 `Int64`와 같습니다.<br>
bit-size를 고를 필요가 없는 상황이라면, `Int`를 쓰세요.

Floating-Point Numbers
---

부동소수 숫자 는 분수로 표현될 숫자를 말합니다. (ex: 3.141592, -0.1 ..)<br>
부동소수 타입은 정수보다 훨씬 넓은 범위의 숫자를 표현합니다. Swift에선 두가지의 부동소수 타입을 지원합니다.<br>
`Double` 은 64-bit 부동소수, `Float`은 32-bit 부동소수 타입을 나타냅니다.

Type Safety and Type Inference 
---

Swift는 *type_safe* 언어입니다. 이는 코드에서 사용할 값의 type에 대해 명확하게 하도록 한다는 뜻 입니다.<br>
`String` 타입을 요구하는 코드라면, 실수로 `Int` 타입을 넘기는 일을 못하도록 합니다.<br>
<br>
따라서 컴파일 시 type check를 수행하고, type이 맞지 않으면 에러를 표시합니다.
이는 다양한 type을 사용하며 작업할때 에러를 막아주지만, 그렇다고 모든 변수와 상수에 type을 지정해 줘야 한다는 뜻은 아닙니다<br>
Swift는 type을 지정하지 않으면, type 추론 (Type inference)를 사용하여 적절한 유형을 찾아냅니다.<br>
컴파일러가 컴파일 시, 자동으로 사용자가 할당한 값을 검사하여 특정 표현식의 type을 추론합니다<br>
Type 추론은, 초기값과 함께 상수/변수를 선언할 때 유용합니다.<br>
다음과 같이 42 라는 값을 새로 선언하는 상수에 할당하면, Swift는 상수에 Int type을 사용하길 원하는구나 라고 유추합니다.
```swift
let meaningOfLife = 42
// meaningOfLife is inferred to be of type Int
```
부동 소수도 마찬가지이고, Swift는 기본적으로 `Double`형태로 유추합니다.
```swift
let pi = 3.14159
// pi is inferred to be of type Double
```
만약 정수와 부동소수 을 혼합하여 계산식을 만든다면, `Double`로 유추 될 것입니다.
```swift
let anotherPi = 3 + 0.14159
// anotherPi is also inferred to be of type Double
```

Numeric Literals
---
정수 literal은 다음과 같이 쓸 수 있다
* 10진수 : no prefix
* 2진수 : 0b prefix
* 8진수 : 0o prefix
* 16진수 : 0x prefix
다음은 `17` 을 여러 literal로 표현한 예시이다.
```swift
let decimalInteger = 17
let binaryInteger = 0b10001       // 17 in binary notation
let octalInteger = 0o21           // 17 in octal notation
let hexadecimalInteger = 0x11     // 17 in hexadecimal notation
```
부동 소수의 경우 10진수(no prefix), 16진수(0x prefix)를 지원한다. 소수점 앞 뒤로 필수로 숫자가 필요하다.<br>
10진수 부동소수의 경우, 대문자 혹은 소문자 `e`를 사용하여 지수표현식이 가능하다. <br>
16진수 부동소수는 필수로 대분자 혹은 소문자 `p`를 사용하여 지수표현식으로 표현해야 한다<br>
10진수 지수표현의 경우 base 숫자에 10^exp를 곱한것이다
* 1.25e2 means 1.25 x 10^2, or 125.0.
* 1.25e-2 means 1.25 x 10^-2, or 0.0125.
16진수 지수표현의 경우 base 숫자에 2^exp를 곱한것이다
* 0xFp2 means 15 x 2^2, or 60.0.
* 0xFp-2 means 15 x 2^-2, or 3.75.
다음은 `12.1875`를 여러 literal로 표현한 예시이다.
```swift
let decimalDouble = 12.1875
let exponentDouble = 1.21875e1
let hexadecimalDouble = 0xC.3p0
```
또한 읽기 쉽도록 하기 위한 추가적인 formatting을 제공한다. 가독성을 높이기 위해 밑줄을 추가 가능하다. 이는 값 자체에 영향을 끼치지 않는다.
```swift
let paddedDouble = 000123.456
let oneMillion = 1_000_000
let justOverOneMillion = 1_000_000.000_000_1
```

Numeric Type Conversion
---

음수가 아닌 정수를 다를때여도, 일반적인 목적의 정수 type 변수,상수를 만들땐 웬만하면 `Int`를 쓰세요<br>
일반적인 상황에서 기본 integer type을 사용하면 코드 내에서 즉시 상호운용 되며, literal 값에서 추론된 type과 일치할 것 입니다.<br>
다른 integer type은 특별히 필요한 때만 쓰세요. (사이즈가 명시적으로 정해져 있거나, 성능, 메모리, 기타 최적화)<br>

### Integer Conversion

정수 타입들마다 담을 수 있는 값의 범위가 다르다<br>
예컨대 `Int8`은 -128~127, `UInt8`은 0~255.<br>
맞지 않는 범위의 값을 할당하려고 하면, 컴파일 시 에러를 뱉습니다.
```swift
let cannotBeNegative: UInt8 = -1
// UInt8 cannot store negative numbers, and so this will report an error
let tooBig: Int8 = Int8.max + 1
// Int8 cannot store a number larger than its maximum value,
// and so this will also report an error
```
유형끼리의 변환을 하기 위해서는, 변환하고자 하는 유형으로 새롭게 초기화를 해야합니다.<br>
아래 예제를 보면 `twoThousand`는 `UInt`type, `one`은 `UInt8`type으로, type이 다르기 때문에 바로 덧셈연산을 할 수 없습니다.<br>
아래처럼 같은 type으로 맞춰주기 위해 기존 값을 기반으로 새로운 값을 생성합니다.
```swift
let twoThousand: UInt16 = 2_000
let one: UInt8 = 1
let twoThousandAndOne = twoThousand + UInt16(one)
```
위에서 `twoThousandAndOne`은 `UInt16`type으로 추론될 것입니다. `SomeType(ofInitialValue)` 는 Swift에서 초기화를 하면서<br>
새로운 값을 전달하는 기본적인 방법입니다. 물론 아무 타입이나 전달 가능한건 아닙니다. `UInt16`에 `UInt8`값을 받아서<br>
초기화하도록 하는 initializer가 구현되어 있기에 사용 가능한 것입니다.<br>
만약 새로운 타입이 수용가능한 initializer를 만들고 싶다면 extension을 사용하면 됩니다. 자세한 내용은 [Extensions]()에서 다룹니다.

### Integer and Floating-Point Conversion
정수와 부동소수점 사이 변환은 명시적이어야 합니다.
```swift
let three = 3
let pointOneFourOneFiveNine = 0.14159
let pi = Double(three) + pointOneFourOneFiveNine
// pi equals 3.14159, and is inferred to be of type Double
```
위 처럼 `three`를 명시적으로 Double로 새롭게 만들어주고 연산을 연산의 양 측이 같은 type이 되어야 합니다.<br>
이런 변환이 없다면, 연산은 허용되지 않을 것 입니다.<br>
반대의 변환(부동소수 to 정수) 도 마찬가지입니다.
```swift
let integerPi = Int(pi)
// integerPi equals 3, and is inferred to be of type Int
```
이렇게 부동소수를 정수로 바꿀때는 소수자리는 잘립니다(내림). 예를들어 4.75는 4가 될 것이고, -3.9는 -3이 됩니다. 

Type Aliases
---

Type aliases (type의 별칭)은 기존 type의 대체 이름을 정의합니다. `typealiase` 키워드를 사용합니다<br>
이를 활용하여, 다른 소스에서 문맥상 더 적절한 이름을 부여하고 사용하는 방식으로 사용할 수 있습니다.
```swift
typealias AudioSample = UInt16

var maxAmplitudeFound = AudioSample.min
// maxAmplitudeFound is now 0
```

Booleans
---
Swift는 Boolean type `Bool`을 지원한다. `true` 혹은 `false` 값을 갖는다.<br>
type-safe한 언어인 Swift이기에, `Bool`대신에 Boolean type이 아닌 값을 사용할 수 없습니다.
```swift
let i = 1
if i {
    // this example will not compile, and will report an error
}
```
다음과 같이 해야겟죠
```swift
let i = 1
if i == 1 {
    // this example will compile successfully
}
```
`i == 1`연산의 결과는 `Bool` type입니다. 연산에 관한 자세한 내용은 [Basic Opertators]()에서 다룹니다.

Tuples
---
튜플은 여러 값을 하나의 복합 값으로 그룹화 합니다. 튜플 내 값은 어떤 유형이든 될 수 있고, 서로 동일한 유형일 필요는 없습니다.
예시에서, (404, "Not Found")는 HTTP 상태 코드를 나타내는 튜플입니다. HTTP 상태코드는 웹페이지를 요청할 때, 웹서버가 반환하는 특정한 값입니다.<br>
404 Not Found는 존재하지 않는 웹페이지를 요청하면 반환되는 값입니다.
```swift 
let http404Error = (404, "Not Found")
// http404Error is of type (Int, String), and equals (404, "Not Found")
```
위 예시에서의 튜플은 `Int`와 `String`의 묶음입니다. 이를 `(Int, String)` type의 튜플 이라고 부를 수 있습니다.<br>
튜플의 별다른 규칙은 없으며 원하는 형태로 type의 순열로 묶고, 나열할 수 있습니다.<br>
<br>
튜플의 내용을 변수/상수로 분해할 수 있습니다. 분해 후 평소 변수/상수를 사용하듯 쓸 수 있습니다.
```swift
let (statusCode, statusMessage) = http404Error
print("The status code is \(statusCode)")
// Prints "The status code is 404"
print("The status message is \(statusMessage)")
// Prints "The status message is Not Found"
```
Tuple의 일부 값만 사용하려면, underscore(\_)를 사용해서 무시하면 된다.
```swift
let (justTheStatusCode, _) = http404Error
print("The status code is \(justTheStatusCode)")
// Prints "The status code is 404"
```
또한 0에서부터 시작하는 인덱스 번호를 사용해서 튜플의 요소들에 접근이 가능하다.
```swift
print("The status code is \(http404Error.0)")
// Prints "The status code is 404"
print("The status message is \(http404Error.1)")
// Prints "The status message is Not Found"
```
튜플을 정의할 때 튜플에 이름 또한 지정할 수 있고, 이름이 지정되면 이름을 통해 접근할 수 있습니다.
```swift
let http200Status = (statusCode: 200, description: "OK")
print("The status code is \(http200Status.statusCode)")
// Prints "The status code is 200"
print("The status message is \(http200Status.description)")
// Prints "The status message is OK"
```
튜플은 특히 함수의 반환값으로 유용합니다. 여러 type의 값을 묶어서도 보낼 수 있으므로, 더욱 유용한 정보를 제공할 수 있습니다.

Optional
---
값이 없는 상황에서 *optional* 을 사용합니다. 이는 두 가지 가능성을 나타내는데요, 값이 있으면 optional을 upwrap하여 해당 값에 엑세스 하거나,<br>
값이 전혀 없는 상황(nil)을 나타낼 수 있습니다.

> optional의 개념은 C/Objective-C에서는 존재하지 않습니다. Objective-C에서 가장 비슷한 것은 갯체를 반환하는 메소드에서 nil을 반환하는 경우 이며,
> 이는 "유효한 객체가 없음"을 의미합니다. 그러나 이는 객체에 대해서만 작동하고, basic C type 혹은 enumeration에선 작동하지 ㅇ낳습니다.
> Objective-C의 경우 일반적으로 값 없음을 나타내기 위해 특수 값(ex: NSNotFound)를 반환하거나 합니다. 이는 함수 호출하는 입장에서 
> 무엇을 리턴할지 알아야 한다는 것이지만, Swift의 optional은 어떤 타입이든 사용 가능합니다.

optional 관련 예를 하나 봅시다. `Int` type은 `String`을 통해 초기화 가능한 initializer를 제공합니다. 그러나 모든 문자열이<br>
converting가능하진 않습니다. `"123"`은 가능하겠지만, `"hello world"`은 안되겠죠.
```swift
let possibleNumber = "123"
let convertedNumber = Int(possibleNumber)
// convertedNumber is inferred to be of type "Int?", or "optional Int"
```
그렇듯, `Int`의 initializer가 실패할 수 있기 때문에 optional Int 를 반환합니다.<br>
Optional Int는 `Int?`로 표기합니다. 물음표는 optional을 의미하며, `Int`값을 가지고 있거나, 값이 없음을 의미합니다.


### nil

optional 값을 값이 없는 상태로 만들고 싶을 때 `nil`을 할당합니다.
```swift
var serverResponseCode: Int? = 404
// serverResponseCode contains an actual Int value of 404
serverResponseCode = nil
// serverResponseCode now contains no value
```
> non-optional 변수에는 `nil` 을 할당할 수 없습니다. nil을 할당 받아야 하는 경우가 있는 변수라면, optional로 만드세요 
기본값을 주지 않고 optional 변수를 만들면 자동으로 nil이 할당 됩니다.
> Swift 의 nil은 Objective-C의 nil과 동일하지 않습니다. Objective-C에서 nil은 존재하지 않는 객체에 대한 포인터입니다.
> Swift에서 nil은 포인터가 아닙니다. 특정 유형의 값이 없는것입니다. 객체만이 아닌, 모든 유형에 사용 가능합니다.

### If Statements and Forced Unwrapping

`if`문을 사용하여 optional 변수가 값을 가지고 있는지 여부를 비교할 수 있습니다. (==)연산자 혹은 (!=)연산자를 통해 `nil`과 비교할 수 있습니다.
```swift
if convertedNumber != nil {
    print("convertedNumber contains some integer value.")
}
```
Optional 변수에 값이 있다고 확신이 든다면 optional 변수 뒤에 느낌표(!)를 붙여 값에 엑세스 할 수 있습니다.<br>
느낌표를 붙이는 것은 "난 이 optional이 명확하게 값이 있다는 것을 안다."라는 뜻이다. 이를 Optional 값의 강제 unwrapping 이라고 한다.

```swift
if convertedNumber != nil {
    print("convertedNumber has an integer value of \(convertedNumber!).")
}
```

`if`문에 대한 자세한 것은 [Control flow]()

### Optional Binding

*Optional binding*을 사용하여 Optional 이 값을 가지고 있는지 확인하고, 가지고 있다면 <br>
non-optional 임시 상수나 변수로 unwrapping하여 사용할 수 있도록 합니다.<br>
Optional binding은 `if`와 `while`문과 함께 사용하여 optional 변수 안의 값을 확인하고, 꺼내어 상수나 변수에 추츨하는 작업을 한번에 합니다.<br>
`if`나 `while`에 대한 자세한 내용은 [Control Flow]()

```swift
if let constantName = someOptional {
    statements
}
```
앞전에 다뤘던 느낌표(!)를 사용한 강제 unwrapping 말고, 아래처럼 사용이 가능해 집니다.
```swift
if let actualNumber = Int(possibleNumber) {
    print("\"\(possibleNumber)\" has an integer value of \(actualNumber)")
} else {
    print("\"\(possibleNumber)\" could not be converted to an integer")
}
// Prints ""123" has an integer value of 123"
```
변환이 성공하면 `actualNumber` 상수는 `if`문 내에서 사용 가능하게 됩니다.<br>
이미 optional 안에 있던 값을 꺼내어 초기화 했기 때문에, ! 를 붙어서 값에 접근할 필요가 없습니다.<br>
Optional binding에는 상수, 변수 둘 다 사용 가능합니다<br>
<br>
하나의 `if`문에 Optional binding 및 Boolean 조건을 원하는 만큼 포함하고, 쉼표로 구분 지을 수 있습니다.<br>
Optional binding의 값 중 하나라도 nil이거나, Boolean 조건이 false라면 `if`문의 전체 조건은 `false`로 간주됩니다.
```swift
if let firstNumber = Int("4"), let secondNumber = Int("42"), firstNumber < secondNumber && secondNumber < 100 {
    print("\(firstNumber) < \(secondNumber) < 100")
}
// Prints "4 < 42 < 100"
 
if let firstNumber = Int("4") {
    if let secondNumber = Int("42") {
        if firstNumber < secondNumber && secondNumber < 100 {
            print("\(firstNumber) < \(secondNumber) < 100")
        }
    }
}
// Prints "4 < 42 < 100"
```
> Optional binding으로 생성된 상수,변수는 `if`문 내에서만 사용할 수 있습니다.
> 반면에, `guard`문으로 생성한 상수,변수는 `guard`문 이후에 오는 코드 행에서 사용 가능합니다.
> 자세한 내용은 [Early Exit]()

### Implicitly Unwrapped Optionals

위에서 설명한 것처럼 Optional 변수는 상수 또는 변수에 값이 없는 상태를 허용합니다. <br>
때로는, Optional이 값이 처음 세팅 된 이후로부터는 항상 값을 가지는 상황을 보장할 수도 있습니다.<br>
이럴 때는, 매번 값에 접근할때마다 확인하고 unwrap하는것을 없애는 것이 유용합니다.<br>
이런 유형의 optional을 *implicitly unwrapped optionals* 라고 합니다.<br>
느낌표 (ex: `String!`)를 뒤에 붙여 implicitly unwrapped optionals 변수를 만들 수 있습니다.<br>
<br>
implicitly unwrapped optionals은 첫 정의 이후부터 값이 있는것을 보장할 수 있을때 사용하는 Optional의 형태이다<br>
사용되는 곳은, 클래스 초기화 중을 생각할 수 있다. 자세한 예시는 <br>
[Automatic Reference Counting - Unowned References and Implicitly Unwrapped Optional Properties
]()<br>
> 이해를 돕기위한 글 : [참고 1](https://stackoverflow.com/questions/24006975/why-create-implicitly-unwrapped-optionals-since-that-implies-you-know-theres)
> [참고 2](https://medium.com/@jongwonwoo/implicitly-unwrapped-optionals%EC%9D%80-%EC%96%B8%EC%A0%9C-%EC%82%AC%EC%9A%A9%ED%95%A0%EA%B9%8C-d1b0f3362182)

implicitly unwrapped optionals은 일반 Optional처럼 nil을 갖지만, <br>
값에 액세스 할 때 non-optional처럼 unwrapping할 필요 없이 접근이 가능합니다.<br>
다음 예제는 일반 `String` 변수에 담기 위해 값에 접근할 때 optional과 implicitly unwrapped optional의 차이를 보여줍니다.
```swift
let possibleString: String? = "An optional string."
let forcedString: String = possibleString! // requires an exclamation mark
 
let assumedString: String! = "An implicitly unwrapped optional string."
let implicitString: String = assumedString // no need for an exclamation mark
```
implicitly unwrapped optional 은 Optional을 사용할 때 마다 <br>
unwrapping 하지 않아도 되는 권한을 부여한 것 이라고 생각할 수 있습니다.<br>
Optional을 사용할 때 마다 뒤에 (!)를 붙이는 것 보다, 선언 시 type 옆에 (!)를 붙여 선언하는게 좋을 수도 있습니다<br>
> implicitly unwrapped optional 이 nil 이고, 이 값에 접근하려고 하면 에러가 발생합니다.
> 이는 값이 없는 일반 Optional 변수 뒤에 (!)를 붙이는 경우도 동일합니다.
implicitly unwrapped optional 또한 검사를 통하거나, Optional binding을 통해<br>
일반 Optional처럼 값이 포함되어 있는지 확인 가능합니다.
```swift
if assumedString != nil {
    print(assumedString!)
}

if let definiteString = assumedString {
    print(definiteString)
}
```
> 향후 nil이 될 가능성이 있는 변수에는 implicitly unwrapped optional을 사용하지 마십시오.

Error Handling
--- 
Error handling을 통해 프로그램 실행 중 발생하는 오류에 대해 처리가 가능합니다.<br>
값의 유무를 판단하여 성공 실패를 판단하던 Optional과는 반대로, error handling은 오류의 근본 원인을 판별하고<br>
필요한 경우 프로그램의 다른 부분으로 오류를 전파합니다.<br>
함수 선언에 `throws`키워드를 포함시켜 오류를 throw할 수 있음을 나타냅니다.<br>
이런 오류를 throw할 수 있는 함수를 사용할 때 `try`키워드를 앞에 추가하여 사용합니다.<br>
```swift
func canThrowAnError() throws {
    // this function may or may not throw an error
}

do {
    try canThrowAnError()
    // no error was thrown
} catch {
    // an error was thrown
}
```
`do` 문은 오류를 하나 이상의 catch에 전달할 수 있는 포함 범위를 만듭니다.
```swift
func makeASandwich() throws {
    // ...
}
 
do {
    try makeASandwich()
    eatASandwich()
} catch SandwichError.outOfCleanDishes {
    washDishes()
} catch SandwichError.missingIngredients(let ingredients) {
    buyGroceries(ingredients)
}
```
예제에서, `makeASandwich()`함수는 사용가능한 깨끗한 접시가 없거나, 재료가 없는 경우 에러를 던질 것입니다.<br>
`makeASandwich()`가 오류를 던질 수 있기 때문에, `try`와 함께 쓰여집니다.<br>
`do`문으로 함수 호출을 래핑하면 throw되는 모든 에러는 `catch`로 전달됩니다.<br>
에러가 없다면, `eatASandwich()`함수가 호출될 것 입니다.<br>
에러가 발생하고, 이 에러가 `SandwichError.outOfCleanDishes` 에러라면 `washDishes()`가 호출될 것이며<br>
에러가 `SandwichError.missingIngredients` 에러라면 `buyGroceries(_:)`가 `catch`패턴에 함께 전달된 `[String]`과 함께 호출될 것이다<br>
더 자세한 내용은 [Error Handling]()

Assertions and Preconditions
--- 
*Assertions* 와 *Preconditions*는 런타임시의 발생하는 것에 대한 검사를 하도록 합니다.<br>
코드를 수행하기 전에 필수 조건이 충족되었는지 확인하기 위해 이 코드를 사용합니다.<br>
assertion 혹은 preconditions 내에 Boolean 조건을 넣어 true라면, 코드 실행이 계속 될 것이며,<br>
조건이 거짓이라면 프로그램의 상태가 invalid하게 됩니다. 이 때 코드 실행은 끝이 나고 app은 terminate 됩니다.<br>
Assertion은 개발 중 실수와 잘못된 조건들을 찾을 수 있으며, Preconditions는 production에서 문제를 발견하도록 돕습니다.<br>
또한 Assertion과 Preconditions는 런타임시의 검증 이외에도, 코드 내에서의 유용한 도큐멘트 형식이 됩니다.<br>
상위의 Error handling에서 다뤘던 에러 조건과 달리, Assertion, Precondition은 복구 가능하거나 예상되는 오류에 사용되지 않습니다.<br>
왜냐하면 Assertion과 precondition은 잘못된 프로그램의 상태를 대변하기 때문에, 그런 경우를 catch하는 방법은 없습니다.<br>
Assertion 과 Precondition의 차이는 그들이 check될 때 입니다. Assertion은 디버그 빌드에서만 검사되지만, Precondition은<br>
Debug 및 Production 빌드에서 모두 검사됩니다.<br>
프로덕션 빌드에서 assertion내의 검사는 수행되지 않기 때문에, 프로덕션 성능에 영향을 주지 않고 개발 단계에서 얼마든지 assertion을 사용할 수 있습니다.<br>

### Debugging with Assertions
Swift 표준 라이브러리의 [assert(_:_:file:line:)](https://developer.apple.com/documentation/swift/1541112-assert)을 사용합니다.<br>
true혹은 false의 결과를 내는 조건식과, false일 경우 표시 할 메시지를 전달합니다. 
```swift
let age = -3
assert(age >= 0, "A person's age can't be less than zero.")
// This assertion fails because -3 is not >= 0.
```
위 예시의 경우 `age`가 음수라면 assertion내 조건은 false가 되고, 프로그램은 종료될 것입니다.<br>
assertion의 실패 메시지는 생략 가능합니다.
```swift
assert(age >= 0)
```
만약 코드에서 이미 조건 검사를 한 경우라면, [assertionFailure(_:file:line:)](https://developer.apple.com/documentation/swift/1539616-assertionfailure)으로 assertion실패를 바로 표현할 수 있습니다.
```swift
if age > 10 {
    print("You can ride the roller-coaster or the ferris wheel.")
} else if age > 0 {
    print("You can ride the ferris wheel.")
} else {
    assertionFailure("A person's age can't be less than zero.")
}
```

### Enforcing Preconditions
[precondition(_:_:file:line:)](https://developer.apple.com/documentation/swift/1540960-precondition)으로 precondition 사용 가능합니다<br>
```swift
// In the implementation of a subscript...
precondition(index > 0, "Index must be greater than zero.")
```
[preconditionFailure(_:file:line)](https://developer.apple.com/documentation/swift/1539374-preconditionfailure)로 이미 조건을 검사한 경우, 실패를 바로 표현할 수 있습니다.

> Uncheck mode(`Ounchecked`)로 컴파일 하면 precondition을 체크하지 않습니다. 컴파일러는 조건이 항상 참이라고 가정하고 코드를 최적화합니다.
> 그러나 `fatalError(_:file:line:)`함수는 최적화 설정과 상관 없이 검사 후 실행을 중지합니다.
> `fatalError(_:file:line:)`을 사용하여 프로토 타이핑 및 초기 개발 중에 구현되지 않은 기능에 대한 stub을 만들 수 있습니다.




