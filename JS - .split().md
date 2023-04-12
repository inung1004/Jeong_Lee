# .split()

<aside> 💡 기준에 의하여 잘라서 배열로 저장

</aside>

```jsx
function solution(my_string) {
    const answer = my_string.replace(/[^0-9]/g, '')
                            .split('')
                            .reduce((acc, curr) => acc + Number(curr), 0);
    return answer;
}
```

### split(1, 2)

첫번째 인자 : 자르는 기준

두번째 인자 : 배열의 길이

```jsx
var str = 'html,css,javascript,jquery,apache,php';
str.split(',') //배열 [html,css,javascript,jquery,apache,php]
str.split(',',2) // 배열 [html,css]
```

### split(’’)

하나하나 잘라서 배열로 저장