# 프로토타입

## 클래스, 객체, 인스턴스 이게 다 뭘까

객체지향 프로그래밍에서 객체는 **변수, 함수, 자료 구조의 조합이 될 수 있는데, 특히 객체지향 프로그래밍에서 클래스를 기반으로 한 변수를 클래스의 인스턴스**라고 지칭한다.

⇒ 우리가 개발을 하면서 접하게 될 프로그래밍에서의 객체는 속성과 기능을 가지는 프로그램 단위를 뜻한다.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/385d647f-4cb5-426b-b55f-fffeaeca742b/Untitled.png)

→ 속성 : 멤버 변수, 파라미터

→ 기능 : 메서드

### 조금 더 세분화해서 살펴보자면

클래스 : 멤버 변수와 메서드를 가지는 객체를 만들기 위한 확장이 가능한 코드 양식, 즉 객체를 찍어내기 위한 틀, 설계도

인스턴스 : 설계도를 바탕으로 실체화되어 메모리에 할당된 실체

### 근데 그럼 인스턴스랑 객체의 차이는 뭐야..?

객체는 소프트웨어 세계의 구현할 대상

인스턴스는 클래스에 따라 소프트웨어 세계에 구현된 실체

<aside> 💡 정리 ✨ 객체 : 소프트웨어 세계에 구현할 대상이며 속성과 기능을 가지는 프로그램 단위 클래스 : 객체에 속성과 기능을 넣어줄 설계도 인스턴스 : 클래스에 따라 메모리상에 구현된 실체

</aside>

# 본격 프로토타입

<aside> 💡 JS는 **객체**를 상속하기 위하여 프로토타입이라는 방식이 존재

</aside>

```jsx
function 기계(){
	this.q = 'strike';
	this.w = 'snowball';
} //이 아이는 복사기계(부모)

var nunu = new 기계(); //nunu에 복사(자식)

console.log(nunu) // 기계 {q: "strike", w: "snowball"}

//**프로토타입**을 사용하여 자식에게 데이터를 물려줄 수 있다. 
```

JS는 프로토타입 기반 언어이다? ⇒ 모든 객체들이 메소드와 속성들을 상속 받기 위한 템플릿으로써 프로토타입 객체를 가진다는 의미

<aside> 💡 상속되는 속성과 메소드들은 각 객체가 아니라 객체의 생성자의  **prototype이라는 속성**에 정의 되어있다.

</aside>

### prototype 속성..?

![prototype 속성.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f5dd9a49-154c-4364-8a8d-1048550c1f37/prototype_%EC%86%8D%EC%84%B1.png)

⇒ 기계에게는 자동으로 prototype 이라는 공간이 생긴다.

JavaScript에서는 함수를 정의하고 파싱단계에 들어가면 **내부적으로 수행되는 작업**이 있다.

⇒ prototype 속성은 **다른 곳에 생성된 함수이름의 프로토타입 객체**를 참조

⇒ 프로토타입 객체의 멤버인 constructor 속성은 함수를 참조하는 내부구조를 가진다.

![함수의 프로토타입 속성이 다른 이름의 프로토타입을 컨스트럭쳐를 통해 가지고 오는 내부 구조.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e19084ce-ef55-4baf-ab3e-40bb8dcdc9f8/%ED%95%A8%EC%88%98%EC%9D%98_%ED%94%84%EB%A1%9C%ED%86%A0%ED%83%80%EC%9E%85_%EC%86%8D%EC%84%B1%EC%9D%B4_%EB%8B%A4%EB%A5%B8_%EC%9D%B4%EB%A6%84%EC%9D%98_%ED%94%84%EB%A1%9C%ED%86%A0%ED%83%80%EC%9E%85%EC%9D%84_%EC%BB%A8%EC%8A%A4%ED%8A%B8%EB%9F%AD%EC%B3%90%EB%A5%BC_%ED%86%B5%ED%95%B4_%EA%B0%80%EC%A7%80%EA%B3%A0_%EC%98%A4%EB%8A%94_%EB%82%B4%EB%B6%80_%EA%B5%AC%EC%A1%B0.png)

<aside> 💡 위에 말들 너무 어려워요 ⇒ prototype은 유전자이다.

</aside>

## prototype에 뭔가를 추가하면?

![nunu.name.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1fd78e9d-6a6c-47cb-bc82-5e992d0a889e/nunu.name.png)

⇒ nunu에 직접적으로 name을 부여한 적이 없음에도 자식(nunu)이 사용가능

### 어떻게 그게 가능한 것인가

⇒ **프로토타입 체인** 덕분

⇒ name이 없으면 부모에게 가서 즉, 부모 유전자(prototype)한테 가서 name을 가져온다.

- **프로토타입 체인**

  프로토타입 객체는 상위 프로토타입으로부터 메서드와 속성을 상속 받을 수도 있고, 그 상위 프로토타입 또한 상속 받을 수 있는 것

  → 다른 객체에 정의된 메서드와 속성을 한 객체에서 사용할 수 있도록 하는 근간

<aside> 💡 직접 자료를 가지고 있으면 ⇒ 출력 없으면 ⇒ 부모 유전자(prototype)에 있는 값 출력 부모 prototype에서도 없으면 ⇒ 부모의 부모 prototype까지 찾아봄

</aside>

## 이론을 들었고 어느정도 이해가 되었으면 Array를 예시로 들어 설명을 해보자

```jsx
var arr = [4, 2, 1]; //우리가 배열을 만드는 방식
var arr = new Array(4, 2, 1); //컴퓨터가 인식해서 배열을 만드는 방식
arr.sort(); //배열을 정렬하는 함수
console.log(arr); //(3) [1, 2, 4] 
```

=⇒ 난 sort() 함수를 만든 기억이 없는데!!! 저게 뭐야..?

그건 바로 **Array의 유전자(prototype)** 덕분

![Array.sort.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f68c746a-9426-486f-98b1-8fc49bf45f44/Array.sort.png)

→ (콘솔창에 Array.prototype을 쳤을 때 나오는 것들) → Array의 유전자

<aside> 💡 New Array 로 인해 arr은 Array의 prototype을 상속받았고, 그것을 사용할 수 있게 됐다.

</aside>

## 응용까지 해보자

⇒ Array가 부모고 모든 배열자료가 상속을 받는다면 아까 기계의 유전자(prototype)에 추가한 것처럼 Array에도 추가할 수 있겠네?

```jsx
var arr = [4, 2, 1];
Array.prototype.getName = function (name) {
	return name;
};
console.log(arr.getName("yoon Ji")); //Yoon Ji
```

→ 위 말대로 getName이라는 함수를 만들어 적용해보았더니 사용이 가능하였다.

## 정리

<aside> 💡 1) 프로토타입 체인은 더 이상 부모가 없을 때까지 진행된다. 2) 부모의 유전자를 콘솔창에 찍어보면 꽤나 많은 유전자들을 확인할 수 있고, 그걸 자식의 자식까지 싹 다 사용할 수 있다. 3) prototype에 직접 무언가를 추가하여도 그 자식을 사용할 수 있다. 4) __proto__는 자식에게 부모의 유전자를 참조하여 사용할 수 있도록 생성된 것, (자식.**proto** == 부모.prototype = true)

</aside>