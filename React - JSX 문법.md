# JSX 문법

- 여러 요소가 있으면 부모 요소로 감싸줘야 함.

```jsx
import React from 'react';

function App() {
  return(
    <div>
      <h1>ㅎㅇ</h1>
      <h2>ㅂㅇ</h2>
    </div>
  ) 
}
import React, { Fragment } from "react";

function App() {
  return(
    <>
      <h1>ㅎㅇ</h1>
      <h2>ㅂㅇ</h2>
    </>
  ) 

} {/*Fragment(<></>)를 사용할 수도 있음*/}
```

- 자바스크립트 표현

→ jsx 내부에서 {} 로 감싸면 됨

```jsx
function App() {
  const name = "리액트";
  return(
    <>
      <h1>{name}</h1>
      <h2>자바스크립트 표현식</h2>
    </>
  );
}
```

- if 문 대신 조건부 연산자

→ if문 사용 x , jsx 밖에서 if문을 사용하거나 {} 안에 조건부 연산자(=삼항연산자) 사용

```jsx
function App() {
  const name = "리액트";
  return (
    <>
      {name === "리액트" ? (
      <h1>리액트입니다.</h1>
      ) : (
      <h1>리액트가 아닙니다.</h1>
      )}
    </>
  );
}
```

- AND 연산자를 사용한 조건부 렌더링

→ 거짓일 때 아무것도 렌더링 하고 싶지 않을 때 조건부 연산자에서는 NULL을 사용할 수도 있지만,  && 연산자를 사용해서 조건부 렌더링을 할 수 있음

```jsx
function App() {
  const name = "리액트";
  return (
    <>
      {name === "리액트" && <h1>리액트입니다.</h1>}
    </>
  ); 
} {/*하지만 Falsy한 값 0은 화면에 나타남*/}
```

- undefined를 렌더링하지 않기

→ 함수에서 undefined만 반환하여 렌더링 하는 상황 X

```jsx
function App() {
  const name = undefined;
  return name; 
} {/*오류남*/}
```

→ 함수가 undefined일 때 나타내고 싶은 문구가 있으면 || 사용

```jsx
function App() {
  const name = undefined;
  return <>{name || '비어있음'}</>
}
```

- 인라인 스타일링

→ DOM 요소에 스타일 적용할 때는 문자열 형태X, 객체형태 O

```jsx
function App() {
  const name = '리액트';
  const style = {
    backgroundColor: 'black'
   // background-color -> backgroundColor 낙타체 사용
  }
  return <div style={style}>{name}</div>;
         //style 객체 선언 후 div에 style값 지정
}
```

- class 대신 className

```jsx
import './App.css' //App.css 불러옴

function App() {
  const name = '리액트';
  return <div className="react">{name}</div>;
}        //className 써서 class를 react로 해줌
//불러온 App.css에서 스타일링 해줄 수 있음
```

- 꼭 닫아야 하는 태그

→ jsx 에서는 태그를 닫지 않으면 오류가 발생함

- 주석

```
{/*이렇게 주석을 넣어야 함*/}
```