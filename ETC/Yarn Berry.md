# Yarn Berry

yarn 2.0 버전부터 등장한 새로운 버전의 yarn

> yarn set version berry
> yarn -v → 2.0보다 높은게 나오면 yarn berry

### 특징

- PnP(Plug & Play): Plug & Play 기능을 도입하여 의존성을 더 효율적으로 관리 → node_modules 폴더가 더 이상 필요하지 않으며, 디스크 공간을 절약합니다.
- \*Zero-install: Zero-install를 지원하여 프로젝트의 의존성을 전역으로 설치하지 않고도 사용할 수 있습니다. 이것은 빠른 시작과 업데이트를 가능하게 합니다.
- 성능 향상: 이전 버전에 비해 훨씬 빠르고 효율적인 성능을 제공합니다

### 장점

- zip 파일yarn berry는 용량 문제를 해결하기 위해 각각의 패키지를 zip 파일로 압축
  → .yarn/cache 디렉토리에 압축된 zip파일들이 저장 → 압축을 통해 node_modules 대비 패키지 용량을 10배 이상 줄입니다.
- \*Zero-install, 패키지의 용량이 줄었기 때문에 패키지를 git에서 관리할 수 있습니다.
  → 레포지토리에 zip파일을 포함시켜서 커밋을 하기때문에 별도로 패키지들을 다운로드할 필요 X
  → .pnp.cjs 파일로 의존성을 관리 → 의존성 탐색 시간 ⬇️
- 동일한 개발 환경, 모든 사용자가 git clone을 통해 같은 zip 파일을 사용합니다.
- 단순한 의존성, 패키지 버전마다 각각의 zip 파일을 만들기 때문에 의존성이 단순 → 의존성으로 인한 여러가지 문제들이 해소 → DX ⬆️

### \*Zero Install (직역: 설치를 하지 않고 이용하는 방식\*\*)

패키지 매니저가 프로젝트의 의존성을 글로벌 또는 로컬 시스템 디렉터리에 설치하지 않고 필요한 패키지를 직접 프로젝트 디렉터리 내에서 관리하는 기술

→ 프로젝트의 의존성을 더 효율적으로 관리하고 프로젝트 간의 의존성 충돌을 방지

→ Yarn Berry에서는 Zero-Install을 기본으로 사용하므로 별도로 설정할 필요 ❌

### \*PnP(Plug & Play)

어떠한 패키지를 설치하게 되면 더 이상 node_modules에 저장되지 않습니다. 대신 .yarn/cache 폴더에 해당 의존성의 정보가 저장되고, 아래와 같이 .pnp.js 파일에 의존성을 찾을 수 있는 정보가 기록

```jsx
["@emotion/css", [\
      ["npm:11.11.2", {\
        "packageLocation": "../../../.yarn/berry/cache/@emotion-css-npm-11.11.2-dbfa42cf83-10c0.zip/node_modules/@emotion/css/",\
        "packageDependencies": [\
          ["@emotion/css", "npm:11.11.2"],\
          ["@emotion/babel-plugin", "npm:11.11.0"],\
          ["@emotion/cache", "npm:11.11.0"],\
          ["@emotion/serialize", "npm:1.1.2"],\
          ["@emotion/sheet", "npm:1.2.2"],\
          ["@emotion/utils", "npm:1.2.1"]\
        ],\
        "linkType": "HARD"\
      }]\
    ]],\
```

→ 각 의존성은 Zip 아카이브\*\*로 관리

## + yarn berry와 monorepo의 관계성

> 보통 모노레포를 구축할 때 yarn berry를 사용하던데 그 이유가 궁금해짐

1. Yarn Berry는 모노레포를 쉽게 관리할 수 있는 Workspaces를 지원, 이를 통해 공통의 종속성을 한 곳에서 관리하고, 패키지 간의 연결을 쉽게 설정 O

### reference

[https://stack94.tistory.com/entry/패키지관리자-yarn-그리고-yarn-berry에-대해서-알아보자#Corepack-1](https://stack94.tistory.com/entry/%ED%8C%A8%ED%82%A4%EC%A7%80%EA%B4%80%EB%A6%AC%EC%9E%90-yarn-%EA%B7%B8%EB%A6%AC%EA%B3%A0-yarn-berry%EC%97%90-%EB%8C%80%ED%95%B4%EC%84%9C-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90#Corepack-1)
