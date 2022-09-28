# 스크롤

! ( 스타일드 컴포넌트 기준 작성 ) !

### 1 ) y축 스크롤 생성

```jsx
export const Test = styled.div`
  overflow-y: scroll;
`
```

→ 근데 이러면 overflow가 안 났음에도 보기 불편하게 스크롤이 존재

```jsx
export const Test = styled.div`
  overflow-y: auto;
`
```

→ 정해놓은 height 을 넘어가면 overflow → 스크롤 생성

### 2 ) 스크롤 기능은 그대로 스크롤바는 없애기

```jsx
export const Test = styled.div`
  overflow-y: scroll;
	::-webkit-scrollbar{
    display : none;
  }
`
```

→ -webkit-scrollbar에서 display : none → 말 그대로 none 사라짐

### 3 ) 스크롤 내가 원하는대로 만들어버리기

```jsx
export const Memos = styled.div`
  display: flex;
  flex-direction: column;
  gap: 20px;
  width: 300px;
  height: 700px;
  overflow-y: auto;
  ::-webkit-scrollbar{
    width: 5px;
    height: 8px;
    background-color: #C8C1AA;
  }
  ::-webkit-scrollbar-thumb {
    background: #113D22;
  }
`
```

![20220928_103641.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bcf628ec-ba6e-4b99-a9eb-77fa95b9e7eb/20220928_103641.png)