Basic Operators
====
[The Swift Programming Language - Basic Operators
](https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/BasicOperators.html)

Operator(연산자)는 값을 확인, 변경, 결합하는데 사용되는 구문이나 특수기호 입니다.<br>
예를 들어 더하기(+) 연산자는 두개의 숫자를 더하고, 논리 연산자 AND (&&)는 두개의 boolean 값을 결합합니다.<br>
Swift는 C표준 연산자를 대부분 지원하며, 코딩 에러를 줄이기 위한 몇몇 향상된 기능을 제공합니다<br>
대입 연산자(=)는 동등 연산자 (==)와 실수로 사용하게 되는 일이 없도록 값을 리턴하지 않습니다.<br>
산술 연산자는 overflow를 감지하여 잘못된 값을 할당하려 할때 막아줍니다.<br>
You can opt in to value overflow behavior by using Swift’s overflow operators, as described in Overflow Operators.<br>
<br>
Swfit는 또한 C에서 제공하지 않는 범위연산자를 제공합니다. (`a..<b` and `a...b`)

Terminology
---
-

Assignment Operator
---
대입연산자는 값을 초기화, 혹은 갱신합니다. `a = b` 는 a의 값을 b의 값으로 초기화 혹은 갱신 합니다.
```swift
let b = 10
var a = 5
a = b
// a is now equal to 10
```

튜플을 할당할 경우 다음과 같이 여러값을 한번에 할당할 수 있습니다.
```swift
let (x, y) = (1, 2)
// x is equal to 1, and y is equal to 2
```
Swift의 대입연산자는 C나 Objective-C처럼 연산자 자체가 값을 반환하지 않습니다. 따라서 다음과 같은 표현은 허용되지 않습니다.
```swift
if x = y {
    // This is not valid, because x = y does not return a value.
}
```

Arithmetic Operators
---

Swift는 기본적으로 오버플로우 연산을 허용하지 않습니다.<br>
Swift의 오버플로우 연산자를 통해 선택적으로 가능합니다 `a &+ b`<br>
[Advanced Operators]()에서 설명합니다.

### Remainder Operator

나머지 연산자 (`%`)
> 다른 언어에선 modulo operator 라고도 하지만, Swift에서 음수로도 작동하는 것은 엄밀히 말하면 나머지 라는 표현이 더 정확합니다
`a%b`의 결과를 계산하기 위해, `%`연산자는 다음 방정식을 풀어 `remainder`를 반환합니다.<br>
`a` = (`b` x `some multiplier`) + `remainder`
9와 4를 대입하면 다음과 같이 되겠죠<br>
9 = (4 x 2) + 1<br>
`a`가 음수일때 계산하면 다음과 같이 같은 방식으로 적용됩니다.
> -9 % 4   // equals -1
-9 와 4 를 대입하여 방정식을 풀면<br>
-9 = (4 x -2) + -1<br>
`b`의 음수값에 대해서는 `b`의 부호는 무시됩니다. `a % b` 과 `a % -b`는 같은 결과를 반환할 것 입니다.<br>
<br>
(중략)

Compound Assignment Operators
---
-

Comparison Operators
---
Swift 는 모든 표준 C 연산자를 제공합니다
> Swift는 식별 연산자 또한 제공합니다. (`===` and `!==`) 두 객체 참조가 같은 객체 인스턴스를 참조하는지 테스트 하는 연산자입니다.
> 자세한건 [Classes and Structures.]()

같은 타입과 같은 갯수의 값을 가지고 있는 두개의 튜플에 대해서도 비교 연산이 가능합니다.<br>
왼쪽부터 하나씩 비교하여, 같지 않을 때 까지 비교합니다. 모든 요소가 같다면 같은 튜플이라고 판단합니다.
```swift
(1, "zebra") < (2, "apple")   // true because 1 is less than 2; "zebra" and "apple" are not compared
(3, "apple") < (3, "bird")    // true because 3 is equal to 3, and "apple" is less than "bird"
(4, "dog") == (4, "dog")      // true because 4 is equal to 4, and "dog" is equal to "dog"
```
튜플 비교는, 튜플 내 값이 연산자에 대해 비교가 가능한 경우에만 가능합니다.
아래 경우엔 Bool값을 대소비교 할 수 없으므로 허용되지 않습니다
```swift
("blue", -1) < ("purple", 1)        // OK, evaluates to true
("blue", false) < ("purple", true)  // Error because < can't compare Boolean values
```
> Swift 표준 라이브러리에서는 7개 미만 튜플에 대해서만 연산자가 구현되어 있습니다. 7개 이상이라면 비교연산자를 직접 구현해야 합니다.

Ternary Conditional Operator
---
-

Nil-Coalescing Operator
---
*nil-coalescing* 연산자(`a ?? b`)는 `a`가 값을 가지고 있으면 랩핑을 해제하고, `a`가 `nil`이라면 default 값으로 `b`를 리턴합니다.<br>
`a`는 Optional이여야 하며, `b`는 `a`와 타입이 일치해야 합니다.<br>
*nil-coalescing* 연산자는 다음 연산의 short-cut이라고 생각하면 됩니다
```swift
a != nil ? a! : b
```

Range Operators
---
Swift는 값의 범위를 나타내기 위한 short-cut형태의 연산자를 제공합니다.

### Closed Range Operator
`a...b`는 `a`부터 `b`까지 포함된 범위를 표현합니다. `a`는 `b`보다 크면 안됩니다.

### Half-Open Range Operator
`a..<b`는 `a`는 포함, `b`는 포함되지 않은 범위를 표현합니다. <br>
마찬가지로 `a`는 `b`보다 크면 안되지만, `a`와`b`가 같다면, 빈 범위를 표현하는 것 입니다.

### One-Sided Ranges
닫힘 범위 연산자는 특정 위치부터 한 방향으로 계속되는 범위를 표현하는 등으로 사용할 수 있을 것 입니다.<br>
(예를 들어 index 2 부터 배열 끝까지...) 이런 경우에는 연산자 한쪽의 값을 생략할 수 있습니다.<br>
이런것을 *one-sided range*라고 합니다.
 ```swift
 for name in names[2...] {
    print(name)
}

for name in names[...2] {
    print(name)
}

for name in names[..<2] {
    print(name)
}
 ```
One-sided ranges can be used in other contexts, not just in subscripts. You can’t iterate over a one-sided range that omits a first value, because it isn’t clear where iteration should begin. You can iterate over a one-sided range that omits its final value; however, because the range continues indefinitely, make sure you add an explicit end condition for the loop.<br>
*one-sided range*에서 다음과 같이 특정 값이 포함되어 있는지 검사할 수 있습니다.
 ```swift
let range = ...5
range.contains(7)   // false
range.contains(4)   // true
range.contains(-1)  // true
 ```

Logical Operators
---
-



