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

# 코틀린에서 지원되는 문법
## Labmda 에서의 암시적 파라메터 네이밍
```kt
ints.filter { it > 0 }
```
스위프트의 `$0, $1, ...` 와 비슷하다.
```swift
ints.filter { $0 > 0 }
```
