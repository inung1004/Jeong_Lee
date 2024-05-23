# .match()

<aside> 💡 찾고 싶은 특정 문자를 찾아서 배열로 반환한다.

</aside>

### 문법

```jsx
str.match(regexp);
```

해당 문자열.match('찾을 단어')\*\*

### 예제

```jsx
let test = "sdf2445sdfsf";
let numArr = test.match(/\\d/g);
console.log(numArr); // ['2', '4', '4', '5']
```

### .match()를 활용한 프로그래머스 문제

https://school.programmers.co.kr/learn/courses/30/lessons/120850

> 문자열 `my_string` 이 매개변수로 주어질 때, `my_string` 안에 있는 숫자만 골라 오름차순 정렬한 리스트를 return 하도록 solution 함수를 작성해보세요.

```jsx
return my_string
  .match(/\\d/g)
  .sort((a, b) => a - b)
  .map(Number);
```

.match()\*\*를 이용해서 숫자만 뽑아내서 배열로 만들어준 뒤,

.sort()로 오름차순 정리 후

.map(Number)숫자배열로 변경
