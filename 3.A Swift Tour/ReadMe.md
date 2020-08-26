# 스위프트 둘러보기

새로운 언어를 배우기 위한 첫 번째 스텝으로, “Hello, world!”를 콘솔로 프린트 해 보아야 하겠죠? Swift는 한 줄로 수행할 수 있습니다.

```
print("Hello, world!")
// "Hello, world!" 라고 프린트 합니다.
```

만약에 C나 Objective-C를 해봤다면, 이 구문은 익숙해보입니다. 스위프트에서 이 한 줄의 코드는 완전한 프로그램입니다.
input, output 또는 문자열 처리를 위해 그 어떤 라이브러리도 가져올 필요가 없습니다. 글로벌 스코프에 작성된 코드는 프로그램의 시작점입니다. 더이상 `main()` 따위 필요하지 않습니다. 그리고 문장 끝에 세미콜론(;)을 더이상 붙이지 않아도 됩니다. 

이 둘러보기에서는 다양한 프로그래밍 작업을 수행하는 방법을 보여주기 때문에 이것만 보아도 코드를 작성해 나가는데 문제가 없습니다. 걱정마세요! 만약에 둘러보기 내용이 이해가 안된다면, 더 자세한 것은 뒤에 더 내용이 있습니다.

익숙해지기 위해 챕터를 Xcode 플레이 그라운드로여세요. 플레이 그라운드를 사용하면 코드 목록을 편집하고 결과를 즉시 볼 수 있습니다.

## Simple Values

### let? var?
상수를 정의할 때에는 `let` 을, 변수를 정의할 때에는 `var`을 사용하세요. 상수값은 컴파일 타임에 알 필요가 없지만, 딱 한 번만 할당해야 합니다. 값의 이름은 한 번 지어주고, 여러군데에서 사용해야 할 때 상수를 사용할 수 있습니다.

```
var myVariable = 42
myVariable = 50 // 변경 가능
let myConstant = 42
// myConstant = 50 -> 컴파일 에러!
```


상수나 변수는 반드시 할당 값과 정의된 타입이 같은 타입이어야 합니다. 그러나 항상 명시적으로 값을 써주지는 않아도 됩니다. 상수나 변수를 만들 때 값을 주면 컴파일러가 값의 타입을 유추합니다. 아래 예를 보면, 컴파일러는 `myVariable`의 초기값이 Integer이기 때문에 그 값이 Integer라고 유추합니다.

```
let implicitInteger = 70
let implicitDouble = 70.0
let explicitDouble: Double = 70
```

> EXPERIMENT
> 명시적으로 Float타입이고 값이 4인 상수를 만들어보세요.
> `let floatConst: Float = 4`


값들은 절대 암시적으로 다른 타입으로 변환되지 않습니다. 만약 값을 다른 타입으로 받고싶다면, 명시적으로 인스턴스를 원하는 타입으로 만드세요.

```
let label = "The width is "
let width = 94
let widthLabel = label + String(width) // Integer 값을 String으로 명시적으로 변환
```

> EXPERIMENT
> 위 예제에서 마지막줄에서 String으로 변환하는 부분을 지우면 어떤 에러가 날까요?!
> `Cannot convert value of type 'Int' to specified type 'String'`


### 문자열?

값을 문자열로 바꾸는 더 간단한 방법이 있습니다! 괄호 안에 값을 쓰고 괄호 앞에 백슬래시를 그어주세요.

```
let apples = 3
let oranges = 5
let appleSummary = "I have \(apples) apples."
let fruitSummary = "I have \(apples + oranges) pieces of fruit."
```


여러 줄을 차지하는 문자열을 표현하기 위해 세개의 쌍따옴표 마크(""")를 사용하세요. 인용구를 닫는 마크와 인던트가 같은 인용구의 시작 줄은 사라집니다.

```
let quotation = """ // this line is removed.
I said "I have \(apples) apples."
And then I said "I have \(apples + oranges) pieces of fruit."
"""
```


### 배열과 딕셔너리

배열이랑 딕셔너리는 []으로 만듭니다. 그리고 엘리먼트들은 [] 속에 인덱스나 키로 접근을 할 수 있습니다. 마지막 엘리먼트에도 콤마(,)를 찍는 것이 가능합니다.

```
var shoppingList = ["catfish", "water", "tulips"]
shoppingList[1] = "bottle of water"

var occupations = [
    "Malcolm": "Captain",
    "Kaylee": "Mechanic",
]
occupations["Jayne"] = "Public Relations"
```


배열은 당신이 엘리먼트를 추가하면 자동으로 커집니다. (사이즈 관리를 따로 할 필요가 없습니다.)
`shoppingList.append("blue paint")

빈 배열이나 딕셔너리를 만들고싶다면, 이니셜라이즈 구문을 사용하세요.
```
let emptyArray = [String]()
let emptyDictionary = [String: Float]()`
```


배열, 딕셔너리 값을 만들 때에나 함수 인자로 넘길 때 타입값을 유추할 수 있는 경우라면, 타입을 명시하지 않아도 됩니다.

```
shoppingList = []
occupations = [:]
```


## Control Flow

조건 체크를 위해 `if`나 `switch`를 사용할 수 있고, 루프가 필요하다면 `for-in`, `while`, `repeat-while`를 사용할 수 있다. 조건이나 루프 값 밖으로 괄호를 치지 않아도 됩니다.(쳐도 상관없음) 그러나 바디에 브레이스는 꼭 필요합니다.. (덧 - 실수를 막을 수 있는 좋은 문법이라고 생각합니다.)
```
let individualScores = [75, 43, 103, 87, 12]
var teamScore = 0
for score in individualScores {
    if score > 50 {
        teamScore += 3
    } else {
        teamScore += 1
    }
}
print(teamScore)
// Prints "11"
```

### if문

`if` 문에서 조건은 무조건 부울 표현식이어야 합니다. `if score { ... }`처럼 암시적으로 true가 아닌 0인지 아닌지 조건을 쓴다면 컴파일 오류가 납니다.

`if`와 `let`을 동시에 쓰며 옵셔널 값이 있는지 없는지 검사할 수 있습니다. 옵셔널 값은 값이 있거나 nil(값이 존재하지 않음)을 표현할 수 있습니다. 물을표 표시를 값에 명시적으로 타입을 주는 경우 타입 뒤에 쓰면 값은 옵셔널 타입으로 만들어집니다.
```
var optionalString: String? = "Hello"
print(optionalString == nil)
// Prints "false"

var optionalName: String? = "John Appleseed"
var greeting = "Hello!"
if let name = optionalName {
    greeting = "Hello, \(name)"
}
```

> EXPERIMENT
> `optionalName`을 nil 값으로 변경해라. 그리고 그 때 인사말을 할 수 있게 핸들링 해보자
> ```
> var optionalName: String?
> var greeting = "Hello!"
> if let name = optionalName {
>     greeting = "Hello, \(name)"
> } else {
>     greeting = "Hello, I do not have name..."
> }
> ```


옵셔널 값이 nil이라면, 조건문은 false가 되고 브레이스 안의 코드는 스킵됩니다.. 그렇지 않으면, optional 값은 unwrapped되고(optional이 if let 혹은 guard let에 의해 optional이 아닌 값이 되는것을 unwrapping이라고 함) let에 상수로 할당되어 블락 안으로 들어갑니다..

옵셔널 값을 핸들링 할 수 있는 또 다른 방법은 `??` 오퍼레이터를 통해 기본값을 제공해 주는 것입니다. 만약에 옵셔널 값이 비어있다면 그 값을 대신해서 기본 값을 사용합니다.

```
let nickname: String? = nil
let fullName: String = "John Appleseed"
let informalGreeting = "Hi \(nickname ?? fullName)"
```


### switch문

`switch`는 정수 타입 뿐 아니라 어떤 종류의 데이터나 다양한 비교 연산자를 지원합니다.

```
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
// Prints "Is it a spicy red pepper?"
```

패턴과 일치하는 값을 상수에 할당하기 위해 패턴에서 let이 어떻게 사용될 수 있는지 보세요. 값이 맞는 스위치 케이스 코드가 실행되고 난 뒤에, 그 뒤 케이스를 계속 실행해 나가지 않습니다. 스위프트에서는 각 케이스가 끝난 뒤에 명시적으로 `break`를 써주지 않아도 됩니다.

### for문
`for-in`를 사용하여 키 벨류 페어를 가지는 딕셔너리 값들을 순회할 수 있습니다. 딕셔너리는 순서가 없는 컬렉션이라 키와 값들은 임의의 순서로 순회됩니다.

```
let interestingNumbers = [
    "Prime": [2, 3, 5, 7, 11, 13],
    "Fibonacci": [1, 1, 2, 3, 5, 8],
    "Square": [1, 4, 9, 16, 25],
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
// Prints "25"
```


### while문
조건을 만족할 때 까지 블럭을 반복 실행하고 싶다면 `while`문을 쓰세요. 대신 루프의 조건이 끝에있을 수 있으므로 루프가 한 번 이상 실행되도록합니다.

```
var n = 2
while n < 100 {
    n *= 2
}
print(n)
// Prints "128"

var m = 2
repeat {
    m *= 2
} while m < 100
print(m)
// Prints "128"
You can keep an index in a loop by using ..< to make a range of indexes.

var total = 0
for i in 0..<4 {
    total += i
}
print(total)
// Prints "6"
Use ..< to make a range that omits its upper value, and use ... to make a range that includes both values.
```