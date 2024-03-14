# .indexOf()

<aside>
💡 특정 문자의 인덱스(위치)를 추출해준다.

</aside>

### 문법

```javascript
string.indexOf(searchvalue, position);
```

searchvalue: 필수로 들어가야 하는 값, 인덱스(위치)를 찾을 문자열

position: 기본값은 0, string에서 searchvalue를 찾기 시작할 위치

### 예제

```javascript
// 문자열
const str = "abcd";
cosole.log(str.indexOf("d")); // 3

// 배열
const arr = [1, 2, 3, 4];
cosole.log(arr.indexOf(4)); // 3

//문자열이나 배열에 찾는 값이 없을 때
cosole.log(arr.indexOf(5)); // -1
```

### 특징

- 찾는 문자열이 없으면 -1을 반환한다.
- 문자열을 찾을 때 대소문자를 구분한다.
- 문자열 또는 배열에서 특정 문자열을 찾고, 검색된 문자열이 제일 처음 나타나는 인덱스(위치)를 리턴한다.

### 프로그래머스

[문제 176963](https://school.programmers.co.kr/learn/courses/30/lessons/176963)

> 사진들을 보며 추억에 젖어 있던 루는 사진별로 추억 점수를 매길려고 합니다. 사진 속에 나오는 인물의 그리움 점수를 모두 합산한 값이 해당 사진의 추억 점수가 됩니다. 예를 들어 사진 속 인물의 이름이 ["may", "kein", "kain"]이고 각 인물의 그리움 점수가 [5점, 10점, 1점]일 때 해당 사진의 추억 점수는 16(5 + 10 + 1)점이 됩니다. 다른 사진 속 인물의 이름이 ["kali", "mari", "don", "tony"]이고 ["kali", "mari", "don"]의 그리움 점수가 각각 [11점, 1점, 55점]]이고, "tony"는 그리움 점수가 없을 때, 이 사진의 추억 점수는 3명의 그리움 점수를 합한 67(11 + 1 + 55)점입니다.
>
> 그리워하는 사람의 이름을 담은 문자열 배열 `name`, 각 사람별 그리움 점수를 담은 정수 배열 `yearning`, 각 사진에 찍힌 인물의 이름을 담은 이차원 문자열 배열 `photo`가 매개변수로 주어질 때, 사진들의 추억 점수를 `photo`에 주어진 순서대로 배열에 담아 return하는 solution 함수를 완성해주세요.

내 **풀이**

1. photo 배열 map
2. photo 배열 map 내에 더해줄 score 생성
3. people 배열 map
4. person을 name에 indexOf 사용해서 위치추출
   1. 여기서 만약 값이 없을 경우를 if를 사용해서 걸러준다. (없을 경우 -1이 반환되기 때문에 이 경우를 이용)
5. 인덱스 추출한 것을 score에 합해준다.
6. answer에 총 score를 push

```javascript
function solution(name, yearning, photo) {
  var answer = [];
  photo.map((people, index) => {
    let score = 0;
    people.map((person) => {
      if (name.indexOf(person) != -1) {
        score += yearning[name.indexOf(person)];
      }
    });
    answer.push(score);
  });
  return answer;
}
```
