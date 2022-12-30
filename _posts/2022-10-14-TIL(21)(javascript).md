---
title: TIL Javascript (19)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 19일차 Promise/ then 메서드
---

# 2022-10-14 TIL

### Promise

---

1. new 로 Promise 객체 생성
2. Promise 객체에서는 executor 라는 함수가 자동으로 실행되고, executor 라는 함수는 resolve 와 reject 라는 두 개의 함수를 인자로 받아서 비동기 처리 함수를 실행
3. executor 를 통해 비동기 처리 함수를 싱행 완료 후, 해당 작업이 성공이면 resolve, tlfvoaus reject 함수를 호출

```jsx
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    let num = 10;
    if (num >= 11) {
      resolve(num);
    } else {
      reject("error");
    }
  }, 1000);
});
```

Promise 의 3가지 상태 (states)

위의 코드에서 promise 변수는 다음과 같이 3가지 상태를 가질 수 있다.

- Pending (대기) : 비동기 처리가 아직 실행되지 않은 상태
- Fulfilled (이행) : 비동기 처리가 성공적으로 완료된 상태
- Rejected (실패) : 비동기 처리가 실패한 상대

### then 매서드

위 코드에서 작업 성공 또는 실패시. 수행할 작업을 정의하고, promise 코드를 실행해주는 메서드

- 두 콜백 함수를 인자로 받은
  - successCallback : 작업 성공 시의 실행 함수
  - failureCallback : 작업 실패 시의 실행 함수

```jsx
promise.then(successCallback, failureCallback);
```

test

```jsx
const promise = new Promise((resolve, reject) = > {
	setTimeout(() => {
		let num = 10;
		if(num >= 11){
			resolve(num);
		}else{
			reject("error");
		}
	}, 1000);
})

promise.then(
	(num) => {
		console.log("success", num);
	},
	(err) => {
		console.log(err);
	}
);
```
