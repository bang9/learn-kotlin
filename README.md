# learn-kotlin
개인적으로 코틀린을 학습하기 위해서 접한 콘텐츠 순서등을 트래킹 하기 위해 기록합니다.


# 라이브 코딩이 가능한 런타임 환경
https://play.kotlinlang.org/

# 기본적으로 매핑되는 문법들 학습하기
link: https://developer.android.com/kotlin/learn?hl=ko

## 상수/변수 선언
```ts
// typescript
let bar: string = 'str';
bar = 'bar';

const foo: number = 3;
// error
foo = 4;
```

```kotlin
// kotlin
var bar: String = "str"
bar = "bar"

val foo: Int = 3
// error
foo = 4
```
## 타입

### Numbers

#### Integer types
|Type|Size(bits)|Min|Max|
|:--:|:--------:|:-:|:-:|
|Byte|8|-128|127|
|Short|16|-32768|32767|
|Int|32|-2^31|2^31-1|
|Long|64|-2^63|2^63-1|

```kt
val one = 1 // Int
val threeBillion = 3000000000 // Long
val oneLong = 1L // Long
val oneByte: Byte = 1
```

#### Floating-point types
|Type|Size(bits)|Significant bits|Exponent bits|Decimal digits|
|:--:|:--------:|:--------------:|:-----------:|:------------:|
|Float|32|24|8|6-7|
|Double|64|53|11|15-16|

```kt
val pi = 3.14 // Double
// val one: Double = 1 // Error: type mismatch
val oneDouble = 1.0 // Double

val e = 2.7182818284 // Double
val eFloat = 2.7182818284f // Float, actual value is 2.7182817
```

> 숫자는 더 큰 유형으로의 암시적 변환 없음. 연산의 경우에는 알아서 컨텍스트에 맞게 변환되어 처리됨
```kt
val l = 1L + 3 // Long + Int => Long
```

> 명시적 변환
```kt
toByte(): Byte
toShort(): Short
toInt(): Int
toLong(): Long
toFloat(): Float
toDouble(): Double
toChar(): Char
```

> nullable 한 숫자는 동일한 값이어도 다른 객체일 수 있음 (메모리 최적화를 위해서 JVM -128~127(byte) 는 같은 객체 사용)
```kt
val a: Int = 100
val boxedA: Int? = a
val anotherBoxedA: Int? = a

val b: Int = 10000
val boxedB: Int? = b
val anotherBoxedB: Int? = b

println(boxedA === anotherBoxedA) // true

println(boxedB == anotherBoxedB) // true
println(boxedB === anotherBoxedB) // false
```

> 리터럴 상수
- Decimals: 123
  - Longs are tagged by a capital L: 123L
- Hexadecimals: 0x0F
- Binaries: 0b00001011

> 연산자
- `+` `-` `*` `/` `%`

> 비교자
- `a == b` `a != b`
- `a < b` `a > b` `a <= b` a >= b`
- `a..b` `x in a..b` `x !in a..b`

> Rules
- `NaN` 은 스스로와 동등하다고 간주
- `NaN` 은 `POSITIVE_INFINITY` 를 포함해서 다른 요소보다 더 큰것으로 간주
- `-0.0` 은 `0.0` 보다 작은것으로 간주

> Unsigned integers
- UByte: an unsigned 8-bit integer, ranges from 0 to 255
- UShort: an unsigned 16-bit integer, ranges from 0 to 65535
- UInt: an unsigned 32-bit integer, ranges from 0 to 2^32 - 1
- ULong: an unsigned 64-bit integer, ranges from 0 to 2^64 - 1

> Unsigneld literals
```kt
val b: UByte = 1u  // UByte, expected type provided
val s: UShort = 1u // UShort, expected type provided
val l: ULong = 1u  // ULong, expected type provided

val a1 = 42u // UInt: no expected type provided, constant fits in UInt
val a2 = 0xFFFF_FFFF_FFFFu // ULong: no expected type provided, constant doesn't fit in UInt

val a = 1UL // ULong, even though no expected type provided and constant fits into UInt
```


## Null safety

### nullable
```ts
// typescript
const nullable?: string = undefined;
```
```kotlin
// kotlin
const nullable: String? = null;
```

### non-null assertion
```ts
// typescript
nullable!.length;
```
```kotlin
// kotlin
nullable!!.length;
```

### optional chaining (safe-call operator)
```ts
// typescript
nullable?.length;
```
```kotlin
// kotlin
nullable?.length;
```

### nullish coalescing (elvis operator)
```ts
// typescript
const len = nullable?.length ?? 0;
```
```kotlin
// kotlin
val len = nullable?.length ?: 0;
```

## 조건문
### if-else
```kt
// 동일
if (condition) {
  // ...
} else if (condition2) {
  // ...
} else {
  // ...
}

val awesome: Boolean = if (lang === "kotlin") {
  true
} else {
  false
}
```

### switch (when)
> https://kotlinlang.org/docs/control-flow.html#when-expression
```ts
// typescript
switch (value) {
  case '1': {
    break; // or return
  }
  case '2': {
    return 'result 2';
  }
  default: {
    // ...
  }
}
```
```kt
// kotlin
when (value) {
  "1" -> {
   // or return
  }
  "2" -> "result 2
  else -> {
    // ...
  }
}

val awesome: Boolean = when (lang) {
  "kotlin" -> true
  else -> false
}
```

## 반복문
### for
```ts
// typescript
for (var x=0; x<=10; x++){
  console.log(x);
}
for (var x=10; x>0; x--){
  console.log(x);
}
```
```kt
// kotlin
for (item in 0..10) println(item)
for (item in 10 downTo 0) println(item)
```

## 코틀린에서 지원되는 문법
### Lambda 에서의 암시적 파라메터 네이밍
```kt
ints.filter { it > 0 }
```
스위프트의 `$0, $1, ...` 와 비슷하다.
```swift
ints.filter { $0 > 0 }
```
