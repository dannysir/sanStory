---
title: TIL Javascript (12)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 12일차 배열 관련 함수 / 삼항연산자
---

# 2022-09-29 TIL

### 배열 관련 함수

---

### forEach

for 문을 대체해서, 간단히 배열의 각 아이템을 가져올 수 있는 함수

```jsx
let SanArray = [1, 2, "SanE", 100];
SanArray.forEach((item) => {
  console.log(item);
});
```

### map

배열의 각 아이템에 정의한 함수를 적용해서, 새로운 배열을 리턴하는 함수

```jsx
const SanArray = [1, 2, "SanE", 100];
const SanArray2 = SanArray.map((item) => item * 2);

console.log(SanArray2);
```

### indexOf

배열에서 지정한 데이터가 위치한 인덱스 번호를 리턴

```jsx
let SanArray = [1, 2, "SanE", 100];
let index = SanArray.indexOf("SanE");
console.log(index);
```

- 결과

```jsx
2;
```

### findIndex

배열의 아이템이 객체일 경우, 해당 객체에서 지정한 데이터 위치를 찾을 수 있는 방법을 제공함

```jsx
const sanArray = [
  {
    id: 1,
    name: "SanE",
  },
  {
    id: 2,
    name: "dannysir",
  },
];

console.log(sanArray[0].indexOf("SanE"));
console.log(sanArray.findIndex((item) => item.name === "SanE"));
```

-

### find

findIndex 와 유사하지만, 지정한 데이터 위치를 리턴하는 것이 아니라, 지정한 데이터가 들어 있는 객체를 리턴함

### filter

배열에서 특정 조건에 맞는 아이템만 추철할 때 사용하는 기능

```jsx
let myArray[1,2,3,4,5,6,7,8,9,10];
let even = myArray.filter(item => item % 2 === 0);
console.log(even);
```

### 삼항 연산자

---

간결한 문법으로, 자주 사용될 수 있음

- 문법

```jsx
condition ? exprIfTrue : exprIfFalse;
```

- 예제
  - 삼항 연산자들 안쓸 시의 코드

```jsx
const myArray = [1, 2];
let descMyArray = "";

if (myArray.length === 0) {
  descMyArray = "빈 배열";
} else {
  descMyArray = "아이템이 있는 배열";
}
console.log(descMyArray);
```

- 동일한 동작을 하는 코드를 삼항 연산자로 작성시

```jsx
const myArray = [1, 2];
let descMyArray = myArray.length === 0 ? "빈배열" : "아이템이 있는 배열";
console.log(descMyArray);
```

### 함수의 기본 인자 (파라미터) 값 설정

- 인자값을 넣지 않을 시의 이슈

```jsx
function printTest(name) {
  console.log(name);
}
printTest();
```

- 디폴트 인자값을 설정

```jsx
function printTest(name = "SanE") {
  console.log(name);
}
printTest();
printTest("dannysir");
```

### 구조 분해 할당 (비구조화 할당) 문법

- 구조 분해 할당은 배열이나 객체의 속성을 해체해서, 값을 개별 변수에 대입 할 수 있게 하는 문법
- 파이썬에서 리스트처럼, javascript 에서는 객체 리터럴 기반 객체와 기반 객체와 배열이 가장 많이 사용되는 데이터 구조이며, 구조 분해 할당은 객체와 배열을 좀 더 쉽게 다루는 문법으로 이해하면 됨

```jsx
let data = {
  name: "SanE",
  age: 26,
};

let { name, age } = data;
// 동일한 프로퍼티 명을 사용해야 해당 프로퍼티에 대입이 된다.
console.log(name, age);

//프로퍼티명과 다른 변수명을 사용하고자 할 때
let { name: myName, age: myAge } = data;
console.log(myName, myAge);

//꼭 객체의 모든 프로퍼티를 가져올 필요는 없다
let { age: old } = data;
console.log(old);
```

- 가져올 프로퍼티가 정의되 있지 않을 경우에는 디폴트 값으로 대입하게 할 수 있음

```jsx
let data = {
  name: "SanE",
  age: 26,
};

let { name, hobby = "basketball" } = data;
console.log(name, hobby);
```

- 가져올 프로퍼티명을 다른 변수에 저장하되, 해당 프로퍼티명이 객체 안에 없을 경우 다른 변수에 디폴트 값을 대입하기
  - 객체 안에 값이 없으면 디폴트 값으로 나타냄

```jsx
let data = {
  name: "SanE",
  age: 26,
};

let { name, age: myAge = 20, hobby = "basketball" } = data;
console.log(name, myAge, hobby);
```
