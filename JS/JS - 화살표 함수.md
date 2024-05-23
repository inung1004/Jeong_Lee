# 🤔 What 화살표 함수

### ‘function’ 이라는 키워드 없이 ‘⇒’ 를 이용해 함수를 생성하는 방법

```jsx
const sum = function (x, y) {
  return x + y;
};

sum(5, 4); //9
```

- 뭣 모르고 사용은 하고 있었으나 화살표 함수가 무엇을 위해 존재하고 기본함수랑 무엇이 다른지 모르고 사용함

---

# 😎 화살표 함수의 특징

## 기본문법 📃

var/let/const 함수명 = (매개변수) ⇒ {실행문}

```jsx
var foo = (a, b) => {
  return (a + b) * 10;
};
```

매개변수가 하나라면?\*\*

⇒ 소괄호 생략 가능

```jsx
var foo = a =>
	return a * 10;
};
```

실행문이 하나라면?\*\*

⇒ 중괄호 생략 가능

⇒ 이 경우, 실행문의 결과가 함수의 반환값

```jsx
var foo = (a, b) => a + b;

foo(1, 2); // 3 반환
```

## 화살표함수는 익명 함수로만 사용 → 함수를 호출하기 위해서는 표현식으로 ✨

### _익명함수? 함수를 재사용하지 않을 목적으로 함수에 이름을 붙이지 않는 것_

### \*표현식? 표현식은 값으로 평가될 수 있는 \*\*문\*\*\*

```jsx
//표현식을 이용한 화살표함수
var addNumber (a, b) => {
  return a + b;
};

//표현식을 이용하지 않은 화살표함수
function (a, b) => {
  return a + b;
};
```

### - 화살표함수는 일반함수보다 간결하게 콜백함수로 사용될 수 있음

```jsx
var numbers = [1, 2, 3, 4, 5];
var newArray = numbers.map((a) => a + a);

console.log(newArray); //[2, 4, 6, 8, 10]
```

## 화살표함수를 사용할 수 없는 경우

- 객체의 메소드를 정의하는 경우
- prototype에 메소드를 할당하는 경우
- 생성자 함수로 사용하는 경우

---

# 🖍 화살표 함수, 그리고 this

화살표 함수의 this → 선언되는 시점에 결정되며 \*\*언제나 상위 스코프의 this를 가리킨다.\*\*

### Because : 화살표 함수에는 _this와 argument 가 없음_\*\*

## 그래서 일반적으로 this 가 개입되는 경우라면 일반함수를 사용

```jsx
var obj = {
  myName: "Barbie",
  logName: function () {
    console.log(this.myName);
  },
};

obj.logName(); //"Barbie"
```

→ 콜백함수로 일반함수표현방식을 사용 → this는 obj가 됨

### 위 예제를 화살표 함수로 표현하면?

```jsx
window.myName = "Hannah";
var obj = {
  myName: "Barbie",
  logName: () => {
    console.log(this.myName);
  },
};

obj.logName();
```

→ 화살표함수를 사용할 경우 this 는 상위스코프의 전역스코프\*\*

### OR

window 객체가 됨

## 화살표함수의 this 바인딩 객체 결정방식은 렉시컬 스코프 유사

### 렉시컬 스코프 ? 함수를 어디에 선언하였는지에 따라 상위스코프가 정해짐 js 비롯 대부분의 프밍언어는 렉시컬 스코프를 따름

### ↔동적스코프

## ⇒ 결론 : 화살표 함수에서 this를 사용할 경우 일반 변수와 동일하게 스코프 체인을 따라 탐색하게 됨

---

# 💫 화살표 함수의 활용

## find

⇒ 테스트 함수 조건을 만족하는 첫번째 엘리먼트 값을 리턴하는 함수

```jsx
const emails = [
  "kim@naver.com",
  "lee@gmail.com",
  "park@google.com",
  "yang@gmail.com",
];

// 일반 함수
const findMail = emails.find(function (email) {
  return email.includes("@gmail.com");
});

// 화살표 함수
const findMail = emails.find((email) => email.includes("@gmail.com"));

console.log(findMail);
// lee@gmail.com
```

→ 화살표 함수를 사용해 같은 내용을 더 간결하게 나타낼 수 있다.

## filter

⇒ 제공된 함수의 조건을 만족하는 모든 엘리먼트로 새로운 배열을 만드는 함수

```jsx
const emails = [
  "kim@naver.com",
  "lee@gmail.com",
  "park@google.com",
  "yang@gmail.com",
];

const noGmail = emails.filter((email) => !email.includes("@gmail.com"));

console.log(noGmail);
// ["kim@naver.com", "park@google.com"]
```

## map

⇒ 배열의 각 요소에 대해 함수를 실핸한 결과 값으로 새로운 배열을 만드는 함수

```jsx
const emails = [
  "kim@naver.com",
  "lee@gmail.com",
  "park@google.com",
  "yang@gmail.com",
];

const id = emails.map((email) => email.split("@")[0]);

console.log(id);
```

---

# 🤔 화살표 함수를 사용하는 이유

### 1 ) 코드의 간결성

1-1) 함수는 가장 많이 사용하는 기능, 하지만 function은 무려 8글자지만 ‘⇒’는 2번만 타이핑 하면 됨

1-2) return 생략 가능

### 2) this 바인딩을 갖지 않음 → 콜백함수의 this와 외부 함수의 this 간 불일치 문제를 해결할 수 있음
