# .join()

<aside> 💡 배열의 모든 요소를 연결해 하나의 문자열로 만든다.

</aside>

### 문법

```jsx
arr.join([separator])
```

separator는 매개변수로, 배열의 각 요소를 구분할 문자열이다.

이 구분자는 필요한 경우 문자열로 변환되고, 생략하면 배열의 원소들의 쉼표로 구분된다

### 예제

```jsx
const love = ['상우', '와', '윤지'];

console.log(love.join());
// 상우,와,윤지

console.log(love.join(''));
// 상우와윤지

console.log(love.join('-'));
// 상우-와-윤지
```

### join()을 사용하는 프로그래머스 문제

https://school.programmers.co.kr/learn/courses/30/lessons/120839

> 가위는 2 바위는 0 보는 5로 표현합니다. 가위 바위 보를 내는 순서대로 나타낸 문자열 `rsp`가 매개변수로 주어질 때, rsp에 저장된 가위 바위 보를 모두 이기는 경우를 순서대로 나타낸 문자열을 return하도록 solution 함수를 완성해보세요.

```tsx
let rspWinner = {
    2: 0,
    0: 5,
    5: 2,
  };

 var answer: string = rsp
   .split("")
   .map((v) => rspWinner[v])
   .join(""); 
```

가위바위보에서 이기는 것만 골라서 키와 값으로 관리하는 **rspWinner 객체**

문자열 rsp를 배열로 바꾸어 하나하나 들어가서 값이 뭔지 확인하게 해주는 **split과 map**

map에서는 인자를 가져와서 rspWinner[v]로 이기는 수로 바꾸어 준 뒤 문자열을 return 해줘야 하기 때문에 **.join()**을 사용한다.