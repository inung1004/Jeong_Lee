# var, let, const 차이

js 에서 변수선언은 선언 → 초기화 단계로 수행

선언단계 : 변수명을 등록, js 엔진에 변수 존재 알림

초기화 단계: 값을 저장하기 위한 메모리 공간 확보, 암묵적 undefined 할당

호이스팅 : 변수 선언이 어디에 있든 상관없이 다른 코드보다 먼저 실행되는 특징

## ! VAR의 문제 ⚠

- 변수 중복 선언 가능하여, 예기치 못한 값을 반환할 수 있다.
- 함수 레벨 스코프로 인해 함수 외부에서 선언한 변수는 모두 전역 변수로 된다.
- 변수 선언문 이전에 변수를 참조하면 언제나 undefined를 반환한다.

### → es6에서 l\*\*et, const\*\*이 나옴

## 본격 var, let, const 차이

### 1. 변수 중복 선언 불가

- var : 변수 중복 선언 가능 → 예기치 못한 값 반환 가능

- let : 변수 중복 선언 불가/재할당 가능

- const : 변수 중복 선언 불가/재할당 불가능

  → 원시값의 재할당 x

  → 객체의 재할당 o

  → 선언과 초기화를 동시에 해야함

  ```jsx
  // 원시값의 재할당
  const name = "kmj";
  name = "howdy"; // 오류

  // 객체의 재할당
  const name = {
    eng: "kmj",
  };
  name.eng = "howdy";

  console.log(name); // output: { eng: "howdy" }
  ```

### 2. 스코프

var → 블록 레벨 스코프\*\*

const, let → 함수 레벨 스코프\*\*

### 3. 변수 호이스팅

- let : 선언 단계와 초기화 단계 분리 → 선언단계가 먼저 실행되지만 초기화 단계는 나중에 돼서 변수 선언 전에 변수에 접근하면 undefined

```jsx
console.log(name); // undefined

let name = "kmj";
```

- const : 선언과 초기화 동시에 진행

```
console.log(name) //초기화가 진행 안 됨

const name = 'kmj'
```
