---
title: TIL Javascript (14)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 14일차 배열 분해 할당
---

# 2022-10-03 TIL

### 배열 분해 할당

---

배열의 각 아이템으 별도 변수에 할당하는 문법

```jsx
let sanArray = [1, 2, 3, 4];
let [fist, second, third, forth] = sanArray;

let [data1, data2] = sanArray;
console.log(data1, data2);

let sanArray2 = ["SanE", "dannysir", "SeoSan"];
let [value1, value2] = sanArray;
console.log(value1, value2);
```

- …을 통해, 나머지 요소를 한번에 가져올 수동 있음

```jsx
let myArray = ["SanE", "danny", "SeoSan", "Alex", "Andy"];
let [item1, item2, ...item3] = myArray;
console.log(item1);
console.log(item2);
console.log(item3);
```

- 결과

```jsx
SanE;
dannysir;
Andy;
```

- 객체와 마찬가지로 기본값을 설정할 수도 있음

```jsx
let myArray1 = [10, 20];
let [item1, item2 = 10, item3 = 20] = myArray1;
console.log(item1, item2, item3);
```

## 유용한 구조 분해 할당 문법 활용 팁

### 변수값 교환하기

---

```jsx
let a = 1;
let b = 2;
[a, b] = [b, a];
console.log(a, b);
```

### 함수 리턴시 여러 데이터 넘겨주기

---

```jsx
function getData() {
  return [10, 20];
}

let [a, b] = getData();
console.log(a, b);
```

### 문자열 분리해서, 각각의 변수에 대입하기

---

- split()
  - 파이썬과 달리, 구분할 인자를 넣어주지 않는다고 해서, 디폴트로’’로 구분되진 않는다. 따라서 명시적으로 ‘ ‘ 를 인자로 넣어줘야 함

```jsx
let data = "Seoul yangchon,mockdong";
console.log(data.split(""));
console.log(data.split(","));
```

- split() 으로 문자열 분리해서, 각각의 변수에 대입하기

```jsx
let data = "Seo San";
let [firstName, lastName] = data.split(" ");
console.log(firstName, lastName);
```
