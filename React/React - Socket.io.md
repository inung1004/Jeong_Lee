# Start 🌱

## Why ⚡️

임베디드와 웹의 만남으로 결성된 프로젝트 JGS에서 사용할 일이 생겼다.

\*_JGS(jointed guard system) ⇒ 지뢰가 밟히면 밟혔다고 웹에서 띄어주는 서비스_

다른 프로젝트에서는 보통 HTTP 통신을 주로 사용 해왔는데 JGS에서는 왜 Socket을 사용하게 되었나?

→ 아래에서 이어서 말하겠다.

## What ⚡️

참고 : [https://helloworld-88.tistory.com/215](https://helloworld-88.tistory.com/215)

### socket.io 란 무엇인가

소켓(Socket)은 프로세스가 드넓은 네트워크 세계로 데이터를 내보내거나 혹은 그 세계로부터 데이터를 받기 위한 실제적인 창구 역할을 한다.

그러므로 프로세스가 데이터를 보내거나 받기 위해서는 반드시 소켓을 열어서 소켓에 데이터를 써보내거나 소켓으로부터 데이터를 읽어들여야 한다.

소켓은 **프로토콜**, **IP 주소**, **포트 넘버**로 정의된다

<aside>
💡 다시말해 소켓은 떨어져 있는 두 호스트를 연결해주는 도구로써 인터페이스의 역할을 한다.

</aside>

## 소켓 통신의 흐름

→ 서버 소켓과 클라이언트 소켓이 있는데 클라이언트 소켓 중점으로 알아보도록 하자
<img width="500" alt="스크린샷 2023-05-18 오후 5 47 26" src="https://github.com/inung1004/Jeong_Lee/assets/101488116/207f452f-447d-4ea4-9eba-d11924eda501">

### 클라이언트 소켓

1. socket() 함수로 가장먼저 소켓을 연다.

2. connect() 함수를 이용하여 통신 할 서버의 설정된 ip와 port 번호에 통신을 시도

3. 통신을 시도 시, 서버가 accept() 함수를 이용하여 클라이언트의 socket descriptor를 반환

4. 이를 통해 클라이언트와 서버가 서로 read(), write() 를 하며 통신 (이 과정이 반복)

### HTTP 통신과 Socket 통신의 차이

**(1) HTTP 통신**

- 클라이언트의 요청이 있을 때만 서버가 응답
- 서버가 응답한 후 연결을 바로 종료하는 단방향 통신이지만 Keep Alive 옵션을 주어 일정 시간동안 커넥션을 유지할 수 있다.
- 실시간 연결이 아닌 데이터 **전달이 필요한 경우에만 요청을 보내는 상황**에 유리
- JSON, HTML, Image 등 다양한 데이터를 주고 받을 수 있다

(2) **Socket 통신**

- 클라이언트와 서버가 특정 포트를 통해 양방향 통신을 하는 방식
- 데이터 전달 후 연결이 끊어지는 것이 아니라 계속해서 연결을 유지 → HTTP에 비해 더 많은 리소스 소모
- 클라이언트와 서버가 **실시간으로 계속하여 데이터를 주고받아야하는 경우**에 유리
- 실시간 동영상 스트리밍이나 온라인 게임 등에 사용

<aside>
💡 JGS의 프로젝트에서는 **실시간**으로 지뢰에 밟혔는지에 대해서 바로바로 알려주어야 한다.
→ 그럼 JGS 프로젝트에는 Socket이 적당한가? HTTP가 적당한가?

</aside>