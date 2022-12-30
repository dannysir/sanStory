---
title: TIL Javascript (18)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 18일차 비동기적 처리/ 콜백 함수
---

# 2022-10-13 TIL

### 주요 비동기적 처리

오래 걸리는 기능은 비동기적으로 처리됨

- Rest API 요청
- 파일/데이터베이스 처리
- 타이머, 암호화 / 복호화 등

### 비동기 처리 예 (setTimeout 함수)

setTimeout()

```jsx
setTimeout(function, milliseconds)
```

- milliseconds : ms 만큼 기다리기
- function : milliseconds 에서 설정한 ms 만큼 기다린 후, 호출하는 함수

코드 예시

```jsx
console.log("SanE");
setTimeout(() => {
  console.log("why me");
}, 1000);
console.log("SeoSan");
```

### 비동기 처리의 문제점

예를 들어, Rest API 를 호출해서 결과값을 받아서, 이를 기반으로 코드를 실행하는 경우를 생각해보기로 하자 이때 해당 함수를 호출한 후, 결과값을 받지 않은 채로, 다음 코드가 실행되면. 전체 코드 실행에 문제가 됨

### 비동기 처리의 문제를 해결할 수 있는 콜백 함수 (Callback Function)

코드 예시

```jsx
function func1() {
  setTimeout(() => {
    console.log(1);
  }, 1000);
}
function func2() {
  console.log(2);
}
func1();
func2();
```

### 콜백 함수 설정

- 자바스크립트에서 함수는 first-class function
  - first-class function 은 파이썬 백엔드 과정에서 설명함
    - 함수 자체를 변수에 저장 가능
    - 함수의 인자에 다른 함수를 인수로 전달 가능
    - 함수의 반환 값(return)으로 함수를 전달 가능

```jsx
function func1(collback) {
  setTimeout(() => {
    console.log("finc1");
  }, 1000);
}
function func2() {
  console.log("func2");
}
func1(func2);
```
