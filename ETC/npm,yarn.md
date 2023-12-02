# npm? yarn?

→ **npm과 yarn은 자바스크립트 런타임 환경인 노드(Node.js)의 패키지 관리자입니다.**

## NPM?

Node Package Manager

### 역할

- **온라인 플랫폼**, 사람들이 노드 패키지를 만들고, 업로드하고, 공유할 수 있는 공간으로 누구나 온라인 플랫폼에 게시된 패키지를 사용할 수 있습니다.
  - 디자인 시스템을 npm에 배포한다고 하는데 여기에 올린다는 말입니다.
- **명령 줄 인터페이스**, 온라인 플랫폼과 상호 작용하기 위해 명령 줄 인터페이스를 사용하며 패키지 설치 및 제거가 가능합니다.
  - ex) npm install styled-components

## Yarn?

페이스북에서 개발한 패키지 관리자

**npm 레지스트리와 호환하면서 속도나 안정성 측면에서 npm보다 향상**

→ npm에 배포된 디자인 시스템도 yarn을 통해 설치할 수 있습니다.

## 차이

### 속도 yarn > npm

패키지 설치 프로세스 처리하는 방법의 차이 때문

npm: 패키지를 한 번에 하나씩 순차적으로 설치

yarn: 여러 패키지를 동시에 가져오고 설치

### 보안 yarn > npm

npm: 자동으로 패키지에 포함된 다른 패키지 코드를 실행

→ 이로 인해 보안 시스템에 몇 가지 취약성이 발생하며 나중에 심각한 문제가 발생할 수 있습니다.

yarn: yarn.lock 또는 package.json파일에 있는 파일만을 설치

### 명령어

| 명령어             | npm                                 | yarn                          |
| ------------------ | ----------------------------------- | ----------------------------- |
| dependencies 설치  | npm install                         | yarn                          |
| 패키지 설치        | npm install [패키지명]              | yarn add [패키지명]           |
| dev 패키지 설치    | npm install --save-dev [패키지명]   | yarn add --dev [패키지명]     |
| 글로벌 패키지 설치 | npm install --global [패키지명]     | yarn global add [패키지명]    |
| 패키지 제거        | npm uninstall [패키지명]            | yarn remove [패키지명]        |
| dev 패키지 제거    | npm uninstall --save-dev [패키지명] | yarn remove [패키지명]        |
| 글로벌 패키지 제거 | npm uninstall --global [패키지명]   | yarn global remove [패키지명] |
| 업데이트           | npm update                          | yarn upgrade                  |
| 패키지 업데이트    | npm update [패키지명]               | yarn upgrade [패키지명]       |

## 결론

yarn이 속도나 보안 측면에서 더 우수하다는 것을 알게되었습니다.

아 근데 또 그렇다고 막 yarn이 npm보다 훨씬 뛰어난 것이다!! 이건 또 아닌 거 같은게 npm 또한 업데이트로 속도나 보안 측면에서 계속적으로 나아지며 yarn과 기능에서의 차이가 얼마 없다고 하기 때문에 개인의 취향에 따라 사용하는 것이 좋을 거 같습니다.
