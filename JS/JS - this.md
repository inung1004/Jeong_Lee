# this

# 01. 상황에 따라 달라지는 this

### this 실행 컨텍스트가 생성될 때 함께 결정된다.

## 01-1. 전역 공간에서의 this

```jsx
var frontGenius = "강석현 선배님";
console.log(frontGenius, this.frontGenius, window.frontGenius); // 강석현 선배님이 3번 나옴
var frontGifted = "정지관";
console.log(frontGifted, this.frontGifted, window.frontGifted); // 정지관이 3번 나옴
var a = 1;
delete window.a; //안 된다
delete a; //이 것 또한 안 된다

window.b = 1;
delete window.b; //된다.
delete b; //된다.
```

<aside> 💡 전역변수를 선언하면 자바스크립트 엔진은 이를 전역객체의 프로퍼티로 할당한다 하지만 delete은 단순 변수선언이 아니라 정확히 객체의 프로퍼티로 할당해주어야 된다

</aside>

## 01-2. 메서드로서 호출할 때 그 메서드 내에서의 this

```jsx
var func = function (x) {
  console.log(this, x);
};
func(1); // Window{ ... } 1

var obj = {
  method: func,
  name: "안윤지",
};
obj.method(2); // method{ name: '안윤지', method: f } 2
obj["method"](3); // method{ name: '안윤지', method: f } 3
```

<aside> 💡 메서드로서 호출한 경우 → 메서드 호출의 주체 (메서드명 앞의 객체) 참조

</aside>

## 01-3. 함수로서 호출할 때 그 함수 내부에서의 this

```jsx
var obj1 = {
  outer: function () {
    console.log(this);
    var innerFunc = function () {
      console.log(this);
    };
    innerFunc(); // 앞에 . 없었으므로 함수로서 호출 this 지정 x

    var obj2 = {
      innerMethod: innerFunc,
    };
    obj2.innerMethod(); // 메서드로서 호출 obj2의 정보
  },
};
obj1.outer(); // 메서드로서 호출 obj1의 정보
// (1) => obj1, (2) => 전역객체(window), (3) => obj2
```

<aside> 💡 함수로서 호출한 경우 → 전역객체를 참조

</aside>
