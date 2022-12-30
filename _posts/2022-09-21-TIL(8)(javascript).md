---
title: TIL Javascript (6)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 6일차 객체
---

# 2022-09-21 TIL

###

## 객체

---

주요 사용법

- 객체 프로퍼티 값 가져오기

```jsx
const MainUser = {
  age: 26,
  name: "SanE",
};

console.log(MainUser);
console.log(MainUser.age);
console.log(MainUser.name);
MainUser.age = 27;
console.log(MainUser.age);
```

- 결과

```jsx
{age: 27, name: "SanE"}
26
SanE
27
```

- 빈 객체 선언 후 , 프로퍼티와 메서드 추가 가능

```jsx
const user = {};
user.name = "SanE";
user.age = 26;
user,get_date = function(){
	return 1 =2;
};
```

- 객체 안에 객체 생성도 가능

```jsx
const MainUser = {
  age: 26,
  name: "SanE",
  otherUser: {
    age: 25,
    name: "Kong",
  },
};
```

- 화살표 함수에서는 this 가 없음
  - 기본적으로 화살표 함수가 가리키는 this 는 function 이 가리키는 this 와 다르지만, 사용하지 않는 편이 헷갈리지 않고 좋다.

```jsx
const MainUser = {
  age: 26,
  name: "SanE",
  get_data: () => this.age,
};
console.log(MainUser.age);
console.log(MainUser.name);
console.log(MainUser.get_data());
```
