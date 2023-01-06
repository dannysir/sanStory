---
title: TIL Javascript (20)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 20일차 콜백 지옥과 Promise/ catch 매서드
---

# 2022-10-18 TIL

<br/>

### 콜백 지옥과 Promise

---

- 테스트

```jsx
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    let num = 10;
    if (num >= 11) {
      /*비동기 작업 성공*/
      resolve(num);
    } else {
      /*비동기 작업 실패*/
      reject("error");
    }
  }, 1000);
});
// 실행 준서에 맞춰줄 필요가 있을 경우 then을 이어서 작성(콜백지옥에서 해방)
promise
  .then((num) => {
    console.log("success", num);
  })
  .then(() => {
    console.log("success", num);
  });
```

### catch 매서드

---

- 실행 중, 예외상황을 처리함
- failureCallback 가 정의되어 있지 않을 경우, reject 시에도 catch 메서드를 호출함

```jsx
// Promise 객체 생성
const promise = new Promise((resolve, reject) => {
  // 비동기 작업 수행
  setTimeout(() => {
    let num = 10;
    if (num >= 11) {
      /* 비동기 작업 성공 */
      resolve(num);
    } else {
      /* 비동기 작업 실패 */
      reject("this is an error");
    }
  }, 1000);
});

promise
  .then((num) => {
    console.log("success", num);
  })
  .catch((error) => {
    console.log(error);
  });
```

결과

```jsx
this is an error
```

chaining

- then 메서드를 연결해서, 순차적으로 실행되어야할 코드를 연결할 수 있음
- then 과 catch 메서드도 함께 연결해서 실행가능함

```jsx
const promise = new Promise((resolve, reject) => {
	console.log("start");
	resolve();
});

promise
	.then(() => {
		console.log("success 1");
		throw new Error("error");
	})
	.catch(err) => {
		console.log(err);
	})
	.then(() => {
		console.log("success 2");
});
```
