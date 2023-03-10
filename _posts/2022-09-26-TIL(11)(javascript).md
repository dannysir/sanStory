---
title: TIL Javascript (9)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 9일차 for문
---

# 2022-09-26 TIL

### for 문

---

```jsx
for ( 초기문; 조건문; 증감문 ) {
	...
}
```

- 초기문: let i = 0; 과 같은 변수 선언을 쓰는 것이 일반적임
- 조건문; i < 5; 와 같이 반복할 조건ㅇ을 쓰는 것이 일반적임
- 증감문; i++; 과 같이 다음 반복 전에 실행되는 구문
- 초기문을 먼저 실행 후, 조건문에 맞으면 반복 1회, 그 다음에 증감문 실행 후, 조건문에 맞으면 다음 반복 실행

```jsx
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

### 배열과 for 문

파이썬에서 리스트 변수의 각 아이템을 꺼내어 반복문으로 실행하는 경우가 많듯이, javascript 도 유사한 기능을 구현 가능

- length 사용 : 배열의 길이만큼 반복하기

```jsx
const data = ["Dave", "Alex", "SanE"];
for (let i = 0; i < data.length; i++) {
  console.log(data[i]);
}
```

- for …of 문 사용하기

```jsx
const data = ["Dave", "Alex", "SanE"];
for (let item of data) {
  console.log(item);
}
```

### 객체와 for 문

- for …in 문으로 객체의 키를 반복할 때마다 가져올 수 있음
- 참고

  - Object.entries(), Object.keys(), Object.values() 을 사용해서, 반복문에 키와 값을 기반으로 사용하는 형태와 유사한 기능을 사용할 수 있음
    - Object.entries : 프로퍼티 키와 값으로 이루어진 각 프로퍼티 셋의 리스트, 즉[[기, 값],[키, 값], [키,값]] 등으로 이루어진 배열 반환
    - Object.keys : 프로퍼티 키 리스트, 즉 [키,키,키] 등으로 이루어진 배열 반환
    - Object.values : 프로퍼티 값 리스트, 즉 [값, 값, 값] 등으로 이루어진 배열 반환

  ```jsx
  const data = {
    name: "SanE",
    age: 26,
    hobby: "basketball",
  };

  console.log(Object.entries(data));
  console.log(Object.keys(data));
  console.log(Object.values(data));
  ```

- for …in 문

```jsx
const data = {
  name: "SanE",
  age: 26,
  hobby: "basketball",
};

for (let key in data) {
  console.log(key);
}

for (let key in data) {
  console.log(data[key]);
}
```
