---
title: TIL Javascript (15)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 15일차 Rest, Spread 파라미터
---

# 2022-10-04 TIL

### Rest 파라미터

---

- Rest 파라미터는 함수 인자 선언 앞에 … 을 붙여서 정의하는 문법
- 해당 함수에 전달된 인자 리스트는 하나의 배열로 해당 변수에 넣어짐

```jsx
function getData(...rest) {
  console.log(rest);
  // typeof 를 사용하면 object 라고 출력되므로, Array.isArray()의 경우 인자값이 배열이면 true를 리턴
  console.log(Array.isArray(rest));
}
getData(10, 20, 30, 40, 50, 60);
```

- 인자의 수만큼 순차적으로 인자값이 대입되고, 나머지만 배열로 대입

```jsx
function getData(a, ...rest) {
  console.log(a);
  console.log(rest);
}
getData(10, 20, 30, 40, 50, 60);
```

결과

```jsx
(10)[(20, 30, 40, 50, 60)];
```

- …변수는 맨 마지막에 와야한다.

### Spread 파라미터

---

- Rest 파라미터와 마찬가지로 …을 붙여서 정의하는 문법
- iterable 한 변수 앞에 붙여서, 해당 변수의 데이터를 개별 아이템으로 분리
  - iterable 이란 반복 가능한 객체를 의미하며, 배열, 문자열 등을 의미함

```jsx
let sanArray = [1, 2, 3];
console.log(...sanArray);
```

- Spread 파라미터 사용이 유용한 경우
  - 함수 인자에 맞추어, 배열의 각 아이템을 대입하고 싶을 경우

```jsx
function san(a, b, c) {
  console.log(a);
  console.log(b);
  console.log(c);
}
const data = [1, 2, 3];
func(...data);
```

기존 배열로 새로운 배열 만들기

```jsx
const myArray1[1, 2, 3];
const myArray2[...myArray1, 4, 5, 6];
console.log(myArray2);
```
