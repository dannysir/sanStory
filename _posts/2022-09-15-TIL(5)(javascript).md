---
title: TIL Javascript (4)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 4일차 조건문과 switch/case 문
---

# 2022-09-15 TIL

### 조건문

---

- 파이썬에서는 탭으로 내부 실행문을 구분했지만, javascript에서는 {}를 통해서 내부 실행문을 구분한다.

> if(조건){

    코드;

}

>

예시)

> let SanAge = 26;
> if(SanAge > 19){

    console.log(”성인입니다.”);

}

>

- if ~ else 구문도 가능함

> if(조건){

    코드;

} else {
코드;
}

>

- elseif 도 가능함

> if(조건){

    코드;

}
elseif(조건){
코드;
}
else{
코드;
}

>

---

### switch / case 문

---

> switch(){

    case 지정값 :
         코드;
         break;
    case 지정값 :
         코드;
         break;
     default:
         코드;

}

>

- case문에서 break를 해주지 않으면, 그 다음 case문과 default 문도 함께 실행하게 된다.
