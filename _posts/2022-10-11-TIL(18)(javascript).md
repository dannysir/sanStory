---
title: TIL Javascript (16)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 16일차 Hoisting 이슈
---

# 2022-10-11 TIL

## Hoisting (호이스팅) 이슈

---

- 호이스팅이란, ‘끌어 올린다’는 의미
- 일반적인 언어는 함수. 변수를 선언한 후. 이후 라인에서 해당 함수와 변수를 사용할 수 있으나. javascript 에서는 함수 또는 변수 선언 전에 해당 함수 또는 변수를 사용해도 에러를 내지 않는 현상을 의미함

### var 키워드

- var 키워드는 let 과 같이 변수 선언에 쓰이는 키워드로, let 과 달리 동일한 이름의 변수를 여러번 선언할 수 있음
  - var 키워드는 참고로만 알아두고, 쓰지 않기로 함

```jsx
var a = 1;
var a = 2;
console.log(a);
```

결과

```jsx
2;
```

### Hoisting 현상과 이유

- Hoisting 현상은 var 키워드와 함수 선언에서만 일어남

```jsx
console.log(a);
a = 10;
console.log(a);
var a = 20;
```

결과

```jsx
underfined;
10;
```

- 위의 예는 다음과 같이 실제로 동작함

```jsx
var a;
console.log(a);
a = 10;
console.log(a);
a = 20;
```

- 함수의 경우도 동일

```jsx
getData();

function getData() {
  console.log("Hello World!");
}
```

- 위의 경우에도 실제로는 함수 선언이 맨 위에서 실행된 후, 다음 코드들이 실행됨

```jsx
function getData() {
  console.log("Hello World");
}
getData();
```

### Hoisting 이유

- javascript 는 함수와 변수 선언을 실행 전, 실행 영역의 맨 앞으로 이동해서 실행함
- javascript 의 변수에 대한 실행 lifecycle 은 다음과 같음
  - 선언 (var a;) - 초기화 (a = 1;) - 사용 (a += 1;)
  - javascript 에서 선언과 초기화 문법을 동시에 쓸 수 있음 (var a = 1;)
  - 하지만, 내부적으로는 javascript 는 함수와 변수 선언 부분만 분리해서, 실행 영역 맨 앞으로 이동해서 실행함
  - 따라서, hoisting 현상이 일어난 변수는 변수를 선어만 한 상태이기 때문에, 아직 값이 초기화되지 않아서, 해당 변수는 undefined 가 들어가 있게 됨

### 해결 방안

1. 변수 선언의 경우, var 키워드는 쓰지 않고, let과 const 만 사용
2. 함수 선언의 경우 함수 표현식으로 사용

```jsx
// 함수 선언문
function getData() {
  console.log("Hello");
}
// 함수 표현식
let getData = function () {
  console.log("Hello");
};
```

- 함수 표현식 사용 예
  - 다음 코드에서 getData 를 var 로 선언할지라도, getData 는 함수가 아닌 변수로 인지하므로 에러가 난다.

```jsx
getData();

let getData() = function() {
	console.log("Hello");
}
```
