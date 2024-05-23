# Start 🌱

## Why ⚡️

동아리에서 개발하고, 현재 유지보수 하고 있는 \*PICK\*\*에 주말 급식이라는 페이지와 여러 기능들이 추가되게 되었다.

\*_PICK ⇒ 기존에 종이로 이루어지던 출석부의 단점들을 분석하고 이를 웹 서비스로 해결하려는 프로젝트_

추가 된 여러 기능들 중 엑셀 다운로드 기능이 있었고, 그렇게 엑셀 다운로드에 도전하게 되었다.

## 시작 전 알아야 할 것⚡️

⇒ 파일을 다운로드 하는 방식은 \*Blob을 활용하는 방법과 File 객체를 활용하는 방법으로 나뉘는데 나는 Blob을 사용하였다.

\*Blob : Blob은 Binary Large Object의 줄임말로 글자 그대로 대용량의 바이너리를 다룰 수 있는 객체

⇒ 이유 : File 객체는 IE와 Edge에서 지원하지 않는다.

### Blob

```jsx
const newBlob = new Blob(array, options);
```

- array ⇒ ArrayBuffer, ArrayBufferView, Blob, DOMstring 등
- options ⇒ 받는 데이터의 타입을 설정해줄 수 있다.

```jsx
// ex)
const blob = new Blob([response.data], {
  type: "application/vnd.openxmlformats-officedocument.spreadsheetml.sheet",
});
```

- array ⇒ 서버에서 넘겨준 response를 넣어주었다.
- options ⇒ type을 .xlsx로 설정해주었다.

→ 참고 : https://minhanpark.github.io/today-i-learned/get-blob-with-axios/

### 그 외에 알아야 할 것 😄

- axios instance ⇒ https://axios-http.com/kr/docs/instance
- useMutation ⇒ [https://velog.io/@kimhyo_0218/React-Query-리액트-쿼리-useMutation-기본-편](https://velog.io/@kimhyo_0218/React-Query-%EB%A6%AC%EC%95%A1%ED%8A%B8-%EC%BF%BC%EB%A6%AC-useMutation-%EA%B8%B0%EB%B3%B8-%ED%8E%B8)
- fileSaver.js ⇒ https://github.com/eligrey/FileSaver.js

# How 🔥\*\*

## 사전설정 🔧

### install

> yarn add file-saver

or TS

> yarn add @types/file-saver

```tsx
// /utils/api/weekendMeal/index.ts
// api 세팅

export const getWeekendMealStudentListExcel = async () => {
  return instance.get("/url", {
    responseType: "blob",
  });
};
```

⇒ responseType을 “blob”으로 지정을 안 해주면 파일이 안 열리는 일이 발생한다…

## 본격 연동 💐

### useMutation을 이용해 onSuccess : response 받아오고 Blob 생성 🪺

```tsx
const { mutate: getExcel } = useMutation(getWeekendMealStudentListExcel, {
  onSuccess: (res) => {
    const blob = new Blob([res.data], {
      type: "application/vnd.openxmlformats-officedocument.spreadsheetml.sheet",
    });
  },
  onError: handleError,
});
```

### fileSaver 사용해서 파일 다운로드 🐣

```tsx
const { mutate: getExcel } = useMutation(getWeekendMealStudentListExcel, {
  onSuccess: (res) => {
    const blob = new Blob([res.data], {
      type: "application/vnd.openxmlformats-officedocument.spreadsheetml.sheet",
    });
    fileSaver.saveAs(blob, "전교생 주말 급식 신청 여부");
    //이 부분이 Blob과 File 객체가 다른 점
    //blob은 파일 이름을 여기서 설정해주지만, File객체는 new File(이 안에서 설정)
  },
  onError: handleError,
});
```

### 전체코드 🐥

```tsx
const { mutate: getExcel } = useMutation(getWeekendMealStudentListExcel, {
  onSuccess: (res) => {
    const blob = new Blob([res.data], {
      type: "application/vnd.openxmlformats-officedocument.spreadsheetml.sheet",
    });
    fileSaver.saveAs(blob, "전교생 주말 급식 신청 여부");
    toast.success("엑셀이 출력되었습니다.", { duration: 1000 });
    // react-hot-toast로 엑셀이 출력됐다고 알려주기
  },
  onError: handleError,
});
```
