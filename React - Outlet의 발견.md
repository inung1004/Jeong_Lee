# 🔍 Outlet의 발견

### 프로젝트를 진행하며 여러 페이지에서 반복적으로 들어가는 컴포넌트를 발견하였는데 이걸 계속 import 해서 쓰기 보다 다른 방법을 찾고자 함

## 내가 원래 알고있던  react-router

```jsx
<BrowserRouter>
      <Header />
      <Routes>
        <Route path='/*' element={<LoginPage />} />
        <Route path='/login' element={<LoginPage />} />
        <Route path='/signup' element={<SignupPage />} />
      </Routes>
</BrowserRouter>
```

### 헤더 컴포넌트를 Routes 밖에 두고 모든 페이지에 적용함

### ⚠︎ 하지만 내가 원한 것은 특정 페이지에는 적용이 되고 그 외에 페이지에는 적용이 안 됐으면 함 → 그래서 찾은 방법 : Outlet

## ❓ Outlet은 무엇인가

→ 부모 라우터 컴포넌트에서 Outlet을 import 해준 후 서브 페이지가 보여질 위치를 Outlet으로 지정해줌

------

# ❗︎ Outlet 사용하여 내가 원하던 문제 해결

------

```jsx
import Header from '@/components/Header';
import { Outlet } from 'react-router-dom';

const MainLayout = () => {
  return (
    <>
      <Header />
	  <Outlet /> //Outlet 사용
    </>
  );
};

export default MainLayout;
```

```jsx
<BrowserRouter>
      <Routes>
        <Route path='/' element={<OpenPage />} />
        <Route path='*' element={<NotFoundPage />} />

        <Route element={<MainLayout />}>
          {/* 헤더가 들어가야 하는 페이지들은 여기에 :) */}
        </Route>

      </Routes>
</BrowserRouter>
```

→ OpenPage, NotFoundPage 에는 헤더 컴포넌트가 적용되지 않지만 MainLayout 안에 있는 페이지들은 헤더 컴포넌트가 적용이 됨