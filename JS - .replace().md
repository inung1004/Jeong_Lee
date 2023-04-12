# .replace()

<aside> 💡 특정 문자를 제거해준다.

</aside>

```jsx
function solution(my_string) {
    return my_string.replace(/[aeiou]/g, '');
}
```

### replace(1,2)

첫번째 인자 : 제거하고 싶은 문자

두번째 인자 : 대체할 문자

없고 그냥 제거하고 싶으면 ‘’을 넣으면 된다.

### /a/g, ''

정규식을 사용 /g는 모든 문자에서 a를 탐색한다.

### /[aeiou]/g, ''

[] 안에 삭제하고 싶은 문자들을 넣으면 한 번에 여러개 삭제 가능하다.

### replace()를 활용한 프로그래머스 문제

https://school.programmers.co.kr/learn/courses/30/lessons/120850

> 문자열 `my_string` 이 매개변수로 주어질 때, `my_string` 안에 있는 숫자만 골라 오름차순 정렬한 리스트를 return 하도록 solution 함수를 작성해보세요.

```jsx
var answer = my_string
    .replace(/[a-z | A-Z]/g, "")
    .split("")
    .map(Number)
    .sort((a, b) => a - b);
```

**.replace()**를 통해 영어를 모두 제거하고,

.split()을 통해 배열로 바꾸어 준 뒤,

.map()을 사용해서 숫자배열로 바꿔준다.

그리고 sort()로 배열을 오름차순으로 정리해준다.