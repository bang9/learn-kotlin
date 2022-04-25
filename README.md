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
