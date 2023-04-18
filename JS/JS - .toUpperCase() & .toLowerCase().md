# .toUpperCase() & `.toLowerCase(`)

<aside> 💡 대문자 & 소문자로 바꿔준다

</aside>

### 문법

```jsx
x.toUpperCase()
```

### 예제

```jsx
let lowStr = "sss";
let upStr = lowStr.toUpperCase();
console.log(upStr); //"SSS"
let changeStr = upStr.toLowerCase();
console.log(changeStr); //"sss"
```

### .toUpperCase() & .toLowerCase()를 활용한 프로그래머스

https://school.programmers.co.kr/learn/courses/30/lessons/120893

> 문자열 `my_string` 이 매개변수로 주어질 때, 대문자는 소문자로 소문자는 대문자로 변환한 문자열을 return하도록 solution 함수를 완성해주세요.

```jsx
function solution(my_string) {
    return my_string
      .split("")
      .map((n) => (n === n.toUpperCase() ? n.toLowerCase() : n.toUpperCase()))
      .join("");
 }
```

split을 통해 글자 하나하나 잘라서 배열로 만들어주고,

map을 통해 배열에 있는 문자 하나하나흘 들어가 대문자로 바꾼 후

대문자로 바꾼 글자와 원래 글자가 같으면 **.toLowerCase()**을 이용해 소문자로 바꿔주고, 원래 글자와 같지 않으면 **.toUpperCase()**를 이용해 대문자로 바꿔준다.