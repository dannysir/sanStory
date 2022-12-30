---
title: Programmers 코딩테스트 (15)
tags: [Programmers, Coding Test]
style: fill
color: light
description: programmers - 최댓값 최솟값 - 문제 풀이
---

# 2022-12-30 TIL

## programmers

### • 최댓값 최솟값

### **문제 설명**

---

문자열 s에는 공백으로 구분된 숫자들이 저장되어 있습니다. str에 나타나는 숫자 중 최소값과 최대값을 찾아 이를 "(최소값) (최대값)"형태의 문자열을 반환하는 함수, solution을 완성하세요.
예를들어 s가 "1 2 3 4"라면 "1 4"를 리턴하고, "-1 -2 -3 -4"라면 "-4 -1"을 리턴하면 됩니다.

### 제한 사항

---

- s에는 둘 이상의 정수가 공백으로 구분되어 있습니다.

### 입출력 예

---

| s             | return  |
| ------------- | ------- |
| "1 2 3 4"     | "1 4"   |
| "-1 -2 -3 -4" | "-4 -1" |
| "-1 -1"       | "-1 -1" |

### 풀이

---

```jsx
function solution(s) {
  let arr = [];
  //split(" ") 을 이용하여 문자열을 배열로
  let San = s.split(" ");
  for (let i = 0; i < San.length; i++) {
    arr.push(parseInt(San[i]));
  }
  //sort()를 이용하여 오름차순으로
  const newArr = arr.sort((a, b) => a - b);
  let answer = `${newArr[0]} ${newArr[newArr.length - 1]}`;
  return answer;
}
```
