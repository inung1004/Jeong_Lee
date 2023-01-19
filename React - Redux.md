# Redux 🎪

⇒ 전역 상태관리 라이브러리

## Flux 데이터 관리? 흐름? 구조부터 살펴보자 🤟 🕶

⇒ 데이터를 많이 감싸고, 상태를 관리하다보면 많은 복면에 닥치게 되는데 그 때 쓰는 구조가 Flux

![Group 1.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/433f91b0-b6b3-4bc9-a15b-3d6f8c4785d7/Group_1.png)

위와 같은 구조를 가지고 있음

근데 왜 갑자기 Redux하다가 Flux..? ⇒ Redux가 Flux를 구현해놓음

<aside> 💡 Redux : Flux를 구현해놓은 구현체

</aside>

### Redux에서 사용되는 Flux

- provider/store → 값을 저장해놓음
- useDispatch/dispatch → 얘를 통해 store가 업데이트 됨
- useSelector → store에 있는 값을 UI가 인지할 수 있도록 하는 것

## React-Redux 왜 사용하는 것인가!! 🙄

1. Redux는 내부적으로 많은 성능 최적화를 구현하므로 자신의 구성 요소가 실제로 필요할 때만 다시 렌더링 → 부담 줄임
2. 레퍼런스가 많음 → 더 쉽게 도움을 요청하고, 잘 쓴 코드를 참고할 수 있음