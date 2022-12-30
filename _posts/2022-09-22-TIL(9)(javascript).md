---
title: TIL Javascript (7)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 7일차 getter와 setter
---

# 2022-09-22 TIL

###

## getter 와 setter

---

- 클래스 기반 객체 지향 문법에서는 클래스 내부 변수를 외부에서 어느 범위까지 접근할 수 있을지를 지정하는 문법을 제공
  - public, private, protected 와 같은 키워드 제공
  - 정보 은닉과 캡슐화 컨셉과 관련 있음
- javascript 객체 리터럴에서는 이와 유사한 기능으로 getter 와 setter 제공

  - getter와 setter 메서드로 표현
  - 메서드를 포함해서, 전체를 프로퍼티라고 할 떄, 프로퍼티를 데이터 프로퍼티 ( 일반적인 프로퍼티), 접근자 프로퍼티 (getter 와 setter)로 나누기도 함
  - getter는 프로퍼티 값을 접근할 때 ( 읽을 때 ) 호출되는 메서드
  - setter는 프로퍼티 값을 수정할 때 ( 설정할 떄 ) 호출되는 메서드

- 예시

```jsx
const SanE = {
	age : 26,
	hometown : Seoul,
	get get_age(){
			return this.age;
			}
	set set _age(value){
			this.age = value
			}
};

console.log(SanE.get_age);
SanE.set_age = 27;
console.log(SanE.get_age);
```

- 결과

```jsx
26;
27;
```

### new Object() 로 생성하는 방식

---

- 기본 객체인 Object()를 기반으로 생성하는 방식

```jsx
const SanE = new Object();
SanE.age = 26;
SanE.hometown = "Mokdong";
console.log(SanE);
```

### 생성자 함수로 생성하는 방식

---

- 생성자 함수는 함수를 의미한다.
- new 함수() 를 쓰면, 객체처럼 사용가능

```jsx
function user(age, name) {
  this.age = age;
  this.name = name;
}
const SanE = new user(25, "SanE");
console.log(SanE.age, SanE.name);
```
