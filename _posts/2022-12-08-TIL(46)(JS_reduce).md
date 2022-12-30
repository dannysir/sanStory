---
title: TIL Javascript (22)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 22일차 reduce()
---

# 2022-12-08 TIL

### reduce()

### 매개변수

---

- callback
  - 배열의 각 요소에 대해 실행할 함수. 다음 네 가지 인수를 받습니다.
- accumulator
  - 누산기는 콜백의 반환값을 누적합니다. 콜백의 이전 반환값 또는, 콜백의 이전 반환값 또는, 콜백의 첫번째 호출이면서 initialValue를 제공한 경우에는 initialValue의 값이다.
- currentValue
  - 처리할 현재 요소
- currentIndex
  - Optional 처리할 현재 요소의 인덱스
  - initialIndex 를 제공한 경우 0, 아니면 1부터 시작합니다.
- array
  - reduce() 를 호출한 배열
- initialValue
  - callback 의 최초 호출에서 첫 번째 인수에서 제공하는 값. 초기값을 제공하지 않으면 배열의 첫 번째 요소를 사용합니다. 빈 배열에서 초기값 없이 reduce()를 호출하면 오류가 발생합니다.

### reduce() 작동 방식

---

```jsx
[0, 1, 2, 3, 4].reduce(function (
  accumulator,
  currentValue,
  currentIndex,
  array
) {
  return accumulator + currentValue;
});
```

설명

| callback   | accumulator | currentValue | currentIndex | array           | 반환 값 |
| ---------- | ----------- | ------------ | ------------ | --------------- | ------- |
| 1번째 호출 | 0           | 1            | 1            | [0, 1, 2, 3, 4] | 1       |
| 2번째 호출 | 1           | 2            | 2            | [0, 1, 2, 3, 4] | 3       |
| 3번째 호출 | 3           | 3            | 3            | [0, 1, 2, 3, 4] | 6       |
| 4번째 호출 | 6           | 4            | 4            | [0, 1, 2, 3, 4] | 10      |

완전한 함수 대신에 화살표 함수를 제공할 수도 있습니다. 아래 코드는 위의 코드와 같은 결과를 반환합니다.

```jsx
[0, 1, 2, 3, 4].reduce((prev, curr) => prev + curr);
```

reduce() 의 두 번째 인수로 초기값을 제공하는 경우, 결과는 다음과 같습니다;

```jsx
[0, 1, 2, 3, 4].reduce(function (
  accumulator,
  currentValue,
  currentIndex,
  array
) {
  return accumulator + currentValue;
},
10);
```

|            | accumulator | currentValue | currentIndex | array           | 반환값 |
| ---------- | ----------- | ------------ | ------------ | --------------- | ------ |
| 1번째 호출 | 10          | 0            | 0            | [0, 1, 2, 3, 4] | 10     |
| 2번째 호출 | 10          | 1            | 1            | [0, 1, 2, 3, 4] | 11     |
| 3번째 호출 | 11          | 2            | 2            | [0, 1, 2, 3, 4] | 13     |
| 4번째 호출 | 13          | 3            | 3            | [0, 1, 2, 3, 4] | 16     |
| 5번째 호출 | 16          | 4            | 4            | [0, 1, 2, 3, 4] | 20     |

### 예제

---

### 배열의 모든 값 합산

```jsx
var sum = [0, 1, 2, 3].reduce(function (accumulator, currentValue) {
  return accumulator + currentValue;
}, 0);
// sum is 6
```

arrow function 으로 작성한 경우

```jsx
var total = [0, 1, 2, 3].reduce(
  (accumulator, currentValue) => accumulator + currentValue,
  0
);
```

### 객체 배열에서의 값 합산

객체로 이루어진 배열에 들어 있는 값을 합산하기 위해서는 반드시 초기값을 주어 각 항목이 여러분의 함수를 거치도록 해야 합니다.

```jsx
var initialValue = 0;
var sum = [{ x: 1 }, { x: 2 }, { x: 3 }].reduce(function (
  accumulator,
  currentValue
) {
  return accumulator + currentValue.x;
},
initialValue);

console.log(sum); // logs 6
```

화살표 함수(arrow function)로도 작성할 수 있습니다:

```jsx
var initialValue = 0;
var sum = [{ x: 1 }, { x: 2 }, { x: 3 }].reduce(
  (accumulator, currentValue) => accumulator + currentValue.x,
  initialValue
);

console.log(sum); // logs 6
```

### 속성으로 객체 분류하기

```jsx
var people = [
  { name: "Alice", age: 21 },
  { name: "Max", age: 20 },
  { name: "Jane", age: 20 },
];

function groupBy(objectArray, property) {
  return objectArray.reduce(function (acc, obj) {
    var key = obj[property];
    if (!acc[key]) {
      acc[key] = [];
    }
    acc[key].push(obj);
    return acc;
  }, {});
}

var groupedPeople = groupBy(people, "age");
// groupedPeople is:
// {
//   20: [
//     { name: 'Max', age: 20 },
//     { name: 'Jane', age: 20 }
//   ],
//   21: [{ name: 'Alice', age: 21 }]
// }
```

### 배열의 중복 항목 제거

```jsx
let arr = [1, 2, 1, 2, 3, 5, 4, 5, 3, 4, 4, 4, 4];
let result = arr.sort().reduce((accumulator, current) => {
  const length = accumulator.length;
  if (length === 0 || accumulator[length - 1] !== current) {
    accumulator.push(current);
  }
  return accumulator;
}, []);
console.log(result); //[1,2,3,4,5]
```
