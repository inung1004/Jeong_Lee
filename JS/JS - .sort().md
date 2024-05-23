# .sort()

<aside>
💡 배열을 정렬해준다

</aside>

### 문법

```javascript
arr.sort([compareFunction]);
```

compareFunction\*\*

- 정렬 순서를 정의하는 함수.\*\*
- 이 값이 생략되면, 배열의 element들은 문자열로 취급되어, 유니코드 값 순서대로 정렬됩니다.
  - ex ) [2, 1, 3, 10].sort() 할 경우 [1, 10, 2, 3] 반환
- 이 함수는 두 개의 배열 element를 파라미터로 입력 받습니다.
- 이 함수가 a, b 두개의 element를 파라미터로 입력받을 경우,
- 이 함수가 리턴하는 값이 0보다 작을 경우,  a가 b보다 앞에 오도록 정렬하고,
- 이 함수가 리턴하는 값이 0보다 클 경우, b가 a보다 앞에 오도록 정렬합니다.
- 만약 0을 리턴하면, a와 b의 순서를 변경하지 않습니다.

새롭게 알게 된 사실 :

- 숫자로 구성된 배열이 아니어도 숫자 올림차순, 내림차순 정렬이 가능하다..!!
- 문자도 abc 순으로 정렬을 해준다

### 예시

```javascript
let numArr = [4, 3, 1, 2];
let strArr = ["ant", "cat", "banana"];

//올림차순 정렬
numArr.sort((a, b) => a - b); // [1, 2, 3, 4]
strArr.sort(); // ["ant", "banana", "cat"];

// 내림차순 정렬
arr.sort((a, b) => b - a); // [4, 3, 2, 1]
strArr.sort(); // ["banana", "cat", "ant"];

//문자인 숫자로 구성된 배열도 정렬이 되드라
let numStrArr = ["1", "3", "2", "4"];
numStrArr.sort(); //["1", "2", "3", "4"]

//객체배열 정렬하기
const obj = [
  { name: "banana", price: 3000 },
  { name: "apple", price: 1000 },
  { name: "orange", price: 500 },
];

obj.sort((a, b) => {
  return a.price - b.price;
});
```

### 프로그래머스

[문제 12933](https://school.programmers.co.kr/learn/courses/30/lessons/12933)

> 함수 solution은 정수 n을 매개변수로 입력받습니다. n의 각 자릿수를 큰것부터 작은 순으로 정렬한 새로운 정수를 리턴해주세요. 예를들어 n이 118372면 873211을 리턴하면 됩니다.

내 풀이

1. 문자열로 변환
2. 배열로 변환 (배열로 변환해주려면 .split(””)을 사용해야 하는데 이건 문자열에서만 가능해서 1. 문자열로 변환)
3. 내림차순으로 정렬
4. 문자열 하나로 합치기
5. 숫자타입으로 바꿔서 반환

```javascript
function solution(n) {
  let answer = n
    .toString()
    .split("")
    .sort((a, b) => b - a)
    .join("");
  //n.toString()말고 n+""해도 문자열로 변환됨.. 첨 알아땅 ㅇㅅㅇ
  return Number(answer);
}
```
