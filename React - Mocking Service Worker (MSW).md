# MSW - Mocking Service Worker ✨

## 실행환경 만들기 🎉

### 1) CRA로 리액트 프로젝트 생성

> npx create-react-app msw

### 2) MSW 설치

> npm install msw

### 3) 서비스 워커 코드 생성

⇒ MSW는 브라우저에서 서비스 워커를 통해서 작동하기 때문에 서비스 워커 등록을 위한 기본적인 코드가 필요

> npx msw init public/ —save

## 본격 시작하기 🎀

<aside> 💡 이 글은 rest 방식을 배경으로 함

</aside>

### 1) src/ 에 mocks 폴더 생성

⇒ 생성 후 mock폴더 안에 handler.js와 browser.js파일 생성

### 2) browser.js

```
import { setupWorker } from "msw";
import {handlers} from "./handlers";

export const worker = setupWorker(...handlers);
```

### 3) handler.js

```jsx
import { rest } from "msw";

const url = process.env.REACT_APP_BASE_URL;

export const handlers = [
  rest.get(`/login`, async (req, res, ctx) => {// '/login'으로 get요청 왔을 때 보내주는 응답
    return res(
      ctx.json({
        id: "f79e82e8-c34a-4dc7-a49e-9fadc0979fda",
        firstName: "John",
        lastName: "Maverick",
      })//json형식으로 위에 값들을 res로 보내줌
    );
  }),

  rest.get(`${url}`, async (req, res, ctx) => {
    const id = req.url.searchParams.get("id"); //쿼리로 보내는 값을 읽을 수도 있음

    const originalResponse = await ctx.fetch(req);
    const originalResponseData = await originalResponse.json();
    //진짜 해당 서버에 요청을 보내 오리지널 응답값을 보내줄 수도 있음
    return res(
      ctx.status(403),
      ctx.json({
        errorMessage: `Data not Found`,
      }) //res로 403 status 보내주고 json형식으로 에러 메시지 보내줌
---------------------------------------------------------------------------------------
      ctx.json({
        data: {
          people: [
            ...originalResponseData.data.people, //오리지널 응답값
            {
              name: id, //아까 쿼리로 보낸  값을 name으로 넣어줌
              age: 17,
            },
          ],
        },
      })
    );
  }),
];
```

### 4) mocking test할 파일 생성

→ src/components/ 에 TestMocking.jsx 파일

```jsx
import { response } from "msw";
import { useState } from "react";

const Item = ({ name, age }) => {
  return (
    <li>
      name : {name} / age : {age}
    </li>
  );
};

const url = process.env.REACT_APP_BASE_URL;

function TestMocking() {
  const [data, setData] = useState(null);
  const [error, setError] = useState(null);

  const handleClick = () => {
    fetch(`url?id=react`) 
      .then((response) => {
        return response.json();
      })
      .then((json) => {
        if (json.errorMessage) {
          throw new Error(json.errorMessage);
        }//errorMessage가 있다면 error 설정해주고
        setData(json.data);
      })
      .catch((error) => {
        setError(`Something Wrong : ${error}`); // 여기서 에러 띄어줌
      });
  };

  const handleClick2 = () => {
    fetch("/login")
      .then((response) => {
        return response.json();
      })
      .then((json) => {
        console.log(JSON.stringify(json));
      });
  };

  if (error) return <p>{error}</p>; //만약 에러가 있다면 위에서 만들 썸띵 어쩌고 띄어줌

  return (
    <div>
      <button onClick={handleClick}>데이터 가져오기</button> {/*url로 보내는 거*/}
      <button onClick={handleClick2}>데이터 가져오기2</button> {/*/login으로 보내는 거*/}
      {data && (
        <ul>
          {data.people.map((person) => (
            <Item
              key={`${person.name}-${person.age}`}
              name={person.name}
              age={person.age}
            />
          ))}
        </ul>
      )}
    </div>
  );
}

export default TestMocking;
```

## 사용 이유 🩰

### 백엔드 API 구현이 완료되기를 기다리느라 에러 처리를 위한 UI도 만들지 못 하고, 혼자 API 연동을 할 수가 없었는데 MSW면 해결 가능 뚝 - 딱 -