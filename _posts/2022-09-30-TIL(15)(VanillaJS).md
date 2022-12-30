---
title: TIL Javascript (13)
tags: [JavaScript, TIL, Web, FrontEnd]
style: fill
color: warning
description: 자바스크립트 공부 13일차 JS document
---

# 2022-09-30 TIL

### 오늘 공부한 JS document

```jsx
const title = document.querySelector("title");
const colorArray = ["back", "pink", "blue", "red", "brown"];

const superEventHandler = {
  handlerMouseEnter: function () {
    title.innerText("Mouse On");
    title.style.color = colorArray[0];
  },
  handlerMouseLeave: function () {
    title.innerText("Mouse leave");
    title.style.color = colorArray[1];
  },
  handlerClick: function () {
    title.style.color = colorArray[2];
  },
  handlerResize: function () {
    document.head.style.backgroundColor = colorArray[3];
    title.style.color = colorArray[4];
  },
};
title.addEventListener("mouseleave", superEventHandler.handlerMouseLeave);
title.addEventListener("mouseenter", superEventHandler.handlerMouseEnter);
title.addEventListener("click", superEventHandler.handlerClick);

window.addEventListener("resize", superEventHandler.handlerResize);

console.log(title);
```

html 에 있는 테그를 JS로 가져오기 위해서는 document를 사용한다.

```jsx
const title = document.querySelector("title");
```

- querySelector 와 getElementById 등등 사용할 수 있다
- querySelector에서 css Selector를 사용해서 html 에 있는 특정 값을 불러 올 수 있다.

## (참고)CSS 전체 selector

---

```jsx
.클래스명    //Class selector
#아이디명    //ID selector
태그명      //태그 selector
*         //전체 selector HTML 문저 전체를 선택
```

## Event

---

document를 이용해서 html 문서를 js 로 가져온 후에 특정 이벤트가 발생 했을 때, 원하는 일이 발생하도록 할 수 있다.

- 예시

```jsx
title.addEventListener("mouseenter", superEventHandler.handlerMouseEnter);
```

다음과 같이 title에 HTML 문서를 가져오고 addEventListener를 통해 “mouseenter”라는 특정 상황에서 superEventHandler.handlerMouseEnter 함수가 실행되도록 할 수 있다.

이벤트 종류 참고

[https://developer.mozilla.org/ko/docs/Web/Events](https://developer.mozilla.org/ko/docs/Web/Events)
