# .reduce()

<aside> 💡 reduce는 배열의 각 요소에 대해 **callback을 실행하며 단 1개의 출력 결과**를 만든다.

즉 **배열 원소를 입력**으로하여 1개의 수치 또는 문자열 또는 배열 또는 딕셔너리를 만든다.

</aside>

### 원소들의 합 구하기

```jsx
let total = [1, 2, 3, 4, 5].reduce(
  ( acc, curr ) => acc + curr, 
  0
);
```

### 배열의 원소들 중 최댓값 구하기

```jsx
let max = [1, 2, 3, 4, 5].reduce(
  ( max, cur ) => Math.max( max, cur ), 
  -Infinity
);
```