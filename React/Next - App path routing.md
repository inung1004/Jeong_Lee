\*페이지 기반 라우팅 이하 ‘페이지’

\*App Path Routing 이하 ‘App’

```bash
❯ cd src/pages
❯ tree
├── _app.tsx
├── _document.tsx
├── dynamic_routing 다이내믹 라우팅
│   ├── [id].tsx /[id] /dynamic_routing/1
│   └── index.tsx /dynamic_routing
├── index.tsx /
├── nested_routing 중첩 라우팅
│   ├── first.tsx /nested_routing/first
│   └── index.tsx /nested_routing
└── static_routing.tsx 정적 라우팅(파일 이름이 곧 path가 됨) /static_routing
```

- `pages` 디렉토리 내부에 있는 파일들이 URL 경로와 직접적으로 매핑
  → ex. `pages/about.tsx` 파일은 `/about` 경로와 매핑
- Dynamic routing을 위해 `[id].tsx`와 같은 파일명을 사용
- 중첩 라우팅은 폴더를 사용하여 구현

```bash
❯ cd src/app
❯ tree
├── dynamic_routing 다이내믹 라우팅
│   ├── [id]
│   │   └── page.tsx /dynamic_routing/1
│   └── page.tsx /dynamic_routing
├── globals.css
├── layout.tsx
├── nested_routing 중첩 라우팅
│   ├── first
│   │   └── page.tsx /nested_routing/first
│   └── page.tsx /nested_routing
│   └── layout.tsx /레이아웃
└── page.tsx /
```

- `app` 디렉토리 내부의 폴더 구조가 URL 경로와 매핑
- 각 폴더 내부에는 `page.tsx` 파일이 있어서 해당 경로의 콘텐츠를 정의
- Dynamic routing은 `[id]`와 같은 폴더명을 사용
- 중첩 라우팅은 폴더 안에 폴더를 생성하여 구현

\*App Path Routing: app 폴더 안에 파일, 폴더를 생성하여 라우팅하는 방식

\*페이지 기반 라우팅: page 폴더 안에 파일, 폴더를 생성하여 라우팅하는 방식

→ 페이지에서 ‘pages’ → ‘app’ 으로 이름만 바뀐 거 아닌가요?

↳ 페이지에서는 파일명이 곧 path였지만, App에서는 폴더명이 path가 됨

→ 페이지에서는 그럼 폴더를 만들 필요가 없는 거 아닌가요?

↳ 중첩 라우팅, 다이내믹 라우팅을 할 때 폴더 필요

→ 둘 다 파일을 생성한다는 점은 같은데 혹시 이 부분에서도 나뉘는게 있나요?

↳ App에서는 page.tsx, 페이지에서는 {path_name}.tsx

⚠️ 무조건 파일 안에서 export를 해줘야 브라우저에서 path에 접근했을때 올바르게 렌더링 된다.

이점 )

(1) 파일 네이밍 규칙 통일: 모든 경로에서 `page.tsx` 파일을 사용하므로 파일 네이밍 규칙이 더 일관되고 통일

(2) 레이아웃 관리: `layout.tsx` 파일을 통해 레이아웃을 쉽게 정의하고 적용

(3) 명확한 디렉토리 구조: 폴더 구조를 통해 경로를 정의하므로, 프로젝트 구조가 더 명확하고 직관적, 특히, 복잡한 중첩 라우팅을 구현할 때 유리
