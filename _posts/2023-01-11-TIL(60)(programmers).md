---
title: Programmers 코딩테스트 (21)
tags: [Programmers, Coding Test, Lv2]
style: fill
color: light
description: programmers LV2 - JadenCase 문자열 만들기 - 문제풀이
---

# 2023-01-11 TIL

<br/>

### • JadenCase 문자열 만들기

<br/>

### **문제 설명**

---

JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다. 단, 첫 문자가 알파벳이 아닐 때에는 이어지는 알파벳은 소문자로 쓰면 됩니다. (첫 번째 입출력 예 참고)

문자열 s가 주어졌을 때, s를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.

### 제한 조건

---

- s는 길이 1 이상 200 이하인 문자열입니다.
- s는 알파벳과 숫자, 공백문자(" ")로 이루어져 있습니다.
  - 숫자는 단어의 첫 문자로만 나옵니다.
  - 숫자로만 이루어진 단어는 없습니다.
  - 공백문자가 연속해서 나올 수 있습니다.

### 입출력 예

---

| s                       | return                  |
| ----------------------- | ----------------------- |
| "3people unFollowed me" | "3people Unfollowed Me" |
| "for the last week"     | "For The Last Week"     |

### 풀이

---

```jsx
function solution(s) {
  //split() 을 이용하여 단어별로 나누어줌
  let sArr = s.split(" ");

  //첫번째 문자가 숫자인지 문자인지 확인 후 대문자로 변경
  for (let i = 0; i < sArr.length; i++) {
    // toLowerCase()를 이용하여 소문자로 변경
    let a = sArr[i].toLowerCase().split("");
    if (!isNaN(a[0])) {
      sArr[i] = sArr[i].toLowerCase();
      // 주의!!!!
      // 공백이 2번 올경우 ' '에 toUpperCase()를 하려하기 때문에 런타임 에러 발생
      // 따라서 길이가 0인 경우 제거
    } else if (isNaN(a[0]) && sArr[i].length != 0) {
      a[0] = a[0].toUpperCase();
      sArr[i] = a.join("");
    }
  }
  let answer = sArr.join(" ");
  return answer;
}
```
