# ๐ Outlet์ ๋ฐ๊ฒฌ

### ํ๋ก์ ํธ๋ฅผ ์งํํ๋ฉฐ ์ฌ๋ฌ ํ์ด์ง์์ ๋ฐ๋ณต์ ์ผ๋ก ๋ค์ด๊ฐ๋ ์ปดํฌ๋ํธ๋ฅผ ๋ฐ๊ฒฌํ์๋๋ฐ ์ด๊ฑธ ๊ณ์ import ํด์ ์ฐ๊ธฐ ๋ณด๋ค ๋ค๋ฅธ ๋ฐฉ๋ฒ์ ์ฐพ๊ณ ์ ํจ

## ๋ด๊ฐ ์๋ ์๊ณ ์๋  react-router

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

### ํค๋ ์ปดํฌ๋ํธ๋ฅผ Routes ๋ฐ์ ๋๊ณ  ๋ชจ๋  ํ์ด์ง์ ์ ์ฉํจ

### โ ๏ธ ํ์ง๋ง ๋ด๊ฐ ์ํ ๊ฒ์ ํน์  ํ์ด์ง์๋ ์ ์ฉ์ด ๋๊ณ  ๊ทธ ์ธ์ ํ์ด์ง์๋ ์ ์ฉ์ด ์ ๋์ผ๋ฉด ํจ โ ๊ทธ๋์ ์ฐพ์ ๋ฐฉ๋ฒ : Outlet

## โ Outlet์ ๋ฌด์์ธ๊ฐ

โ ๋ถ๋ชจ ๋ผ์ฐํฐ ์ปดํฌ๋ํธ์์ Outlet์ import ํด์ค ํ ์๋ธ ํ์ด์ง๊ฐ ๋ณด์ฌ์ง ์์น๋ฅผ Outlet์ผ๋ก ์ง์ ํด์ค

------

# โ๏ธ Outlet ์ฌ์ฉํ์ฌ ๋ด๊ฐ ์ํ๋ ๋ฌธ์  ํด๊ฒฐ

```jsx
import Header from '@/components/Header';
import { Outlet } from 'react-router-dom';

const MainLayout = () => {
  return (
    <>
      <Header />
	  <Outlet /> //Outlet ์ฌ์ฉ
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
          {/* ํค๋๊ฐ ๋ค์ด๊ฐ์ผ ํ๋ ํ์ด์ง๋ค์ ์ฌ๊ธฐ์ :) */}
        </Route>

      </Routes>
</BrowserRouter>
```

โ OpenPage, NotFoundPage ์๋ ํค๋ ์ปดํฌ๋ํธ๊ฐ ์ ์ฉ๋์ง ์์ง๋ง MainLayout ์์ ์๋ ํ์ด์ง๋ค์ ํค๋ ์ปดํฌ๋ํธ๊ฐ ์ ์ฉ์ด ๋จ
