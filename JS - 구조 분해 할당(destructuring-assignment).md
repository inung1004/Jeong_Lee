# 구조 분해 할당(destructuring-assignment)

### 구조 분해 할당 구분은 배열이나 객체의 속성을 해체하여 그 값을 개별 변수에 담을 수 있게 하는 JavaScript 표현식

<aside> 💡 **객체나 변수로 분해할 수 있게 해주는  특별한 문법**

</aside>

# 🤔 What 구조 분해 할당

### 객체 및 배열 리터럴 표현식을 사용하면 즉석에서 쉽게 데이터 뭉치를 만들 수 있다.

```jsx
var x = [1, 2, 3, 4, 5];
var [y, z] = x;
console.log(y); // 1
console.log(z); // 2
```

<aside> 💡 할당문의 좌변에서 사용하여, 원래 변수에서 어떤 값을 분해해 할당할지 정의한다.

</aside>

------

# 😎 화살표 함수의 특징

## 배열 구조 분해

### 기본 변수 할당 📃

```jsx
var num = ["one", "two", "three"];

var [red, yellow, green] = num;
console.log(red); // "one"
console.log(yellow); // "two"
console.log(green); // "three"
var a, b;

[a, b] = [1, 2];
console.log(a); // 1
console.log(b); // 2
```

→ 변수의 선언이 분리되어도 구조 분해를 통해 값을 할당할 수 있다.

### 기본값 📃

```jsx
var a, b;

[a=5, b=7] = [1];
console.log(a); // 1
console.log(b); // 7
```

→ 변수에 기본값 할당 → 분해한 값이 undefined일 때 그 값을 대신 사용한다.

### 변수 값 교환하기 📃

```jsx
var a = 1;
var b = 3;

[a, b] = [b, a];
console.log(a); // 3
console.log(b); // 1
```

### 함수가 반환한 배열 분석 📃

```jsx
function study() {
  return ["전영준 선배님", "김소연", "정지관", "강석현 선배님", "김철우"];
}

var a, b, c, d;
[a, , b, c, d] = study();
console.log(a); // '전영준 선배님'
console.log(b); // '정지관'

[,,] = study(); // 반환 값 모두 무시 가능
```

→ 구조 분해를 사용하면 반환된 배열에 대한 작업을 더 간결하게 수행할 수 있다.  ⇒ 위 예제에서 study() 는 출력으로 배열을 반환하는데, 하나의 구조 분해만으로 값을 분석

→ [a, , b, c] 로 필요하지 않은 반환 값을 무시할 수 있다.

### 변수에 배열의 나머지를 할당하기 📃

```jsx
var [a, ...b] = [1, 2, 3];
console.log(a); // 1
console.log(b); // [2, 3]
```

→ 배열을 구조 분해할 경우, 나머지 구문을 이용해 분해하고 남은 부분을 하나의 변수에 할당할 수 있다.

<aside> 💡 **!! 나머지 요소의 오른쪽 뒤에 쉼표가 있으면 SyntaxError 가 발생한다.**

</aside>

### 정규 표현식과 일치하는 값 해체하기 📃

```jsx
function parseProtocol(url) {
  var parsedURL = /^(\\w+)\\:\\/\\/([^\\/]+)\\/(.*)$/.exec(url);
  if (!parsedURL) {
    return false;
  }
  console.log(parsedURL); // ["<https://developer.mozilla.org/en-US/Web/JavaScript>", "https", "developer.mozilla.org", "en-US/Web/JavaScript"]

  var [, protocol, fullhost, fullpath] = parsedURL;
  return protocol;
}

console.log(parseProtocol('<https://developer.mozilla.org/en-US/Web/JavaScript>')); // "https"
```

[정규표현식 ](https://www.notion.so/4fd42d6bb6f64ba3b3f49d0a43591998)

→ exec() 메서드는 일치하는 부분를 찾으면 그 문자열에서 정규식과 일치하는 부분 전체를 배열의 맨 앞에, 그리고 그 뒤에 정규식에서 괄호로 묶인 각 그룹과 일치하는 부분을 포함하는 배열을 반환

## 객체 구조 분해

### 기본 할당 📃

```jsx
var o = {p: 42, q: true};
var {p, q} = o;

console.log(p); // 42
console.log(q); // true
```

### 선언없는 할당 📃

```jsx
var a, b;

({a, b} = {b: 1, a: 2});

console.log(a, b); // 2 1
```

→ 구조 분해를 통해 변수의 선언과 분리하여 변수에 값 할당 가능

### 새로운 변수 이름으로 할당하기 📃

```jsx
var o = {p: 42, q: true};
var {p: foo, q: bar} = o;

console.log(foo); // 42
console.log(bar); // true
```

→ 객체로부터 속성을 해체하여 객체의 원래 속성명과는 다른 이름의 변수에 할당할 수 있다.

### 기본값 📃

```jsx
var {a = 10, b = 5} = {a: 3};

console.log(a); // 3
console.log(b); // 5

var {a: aa = 10, b: bb = 5} = {a: 3}; //기본값 갖는 새로운 이름의 변수에 할당하기

console.log(aa); // 3
console.log(bb); // 5 
```

→ 객체로부터 해체된 값이 undefined인 경우, 변수에 기본값을 할당할 수 있다.

→ 새로운 변수명 할당과 기본값 할당을 한번에 할 수 있다.

------

# 🤔 구조 분해 할당을 사용하는 이유

→ 함수에 객체나 배열에 저장된 데이터 전체가 아닌, 일부만 전달하고 싶을 때

⇒ 이럴 때 객체나 배열을 변수로 '분해'할 수 있게 해준다.

```jsx
let arr = ["YoonJi", "Ahn"]
let [firstName, surName] = arr;
 
alert(firstName); //YoonJi
alert(serName);   //Ahn
 
//구조 분해 할당을 사용하지 않으면 밑에처럼 직접할당해야한다.
 
// let [firsName, surname] = arr;
let firstName = arr[0];
let surname = arr[1];
```

<aside> 💡 객체와 배열은 JS에서 가장 많이 쓰이는 자료구조이다. 이런 객체와 배열을 더욱 유용하게 사용할 수 있도록 돕는 것이 구조 분해 할당이다.

</aside>