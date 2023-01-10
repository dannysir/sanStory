---
title: Programmers 코딩테스트 (20)
tags: [Programmers, Coding Test, 2018 KAKAO BLIND RECRUITMENT]
style: fill
color: light
description: 2018 KAKAO BLIND RECRUITMENT - [1차 다트게임]
---

# 2023-01-10 TIL
<br/>

### • [1차] 비밀지도
<br/>
### **문제 설명**

---

카카오톡 게임별의 하반기 신규 서비스로 다트 게임을 출시하기로 했다. 다트 게임은 다트판에 다트를 세 차례 던져 그 점수의 합계로 실력을 겨루는 게임으로, 모두가 간단히 즐길 수 있다.갓 입사한 무지는 코딩 실력을 인정받아 게임의 핵심 부분인 점수 계산 로직을 맡게 되었다. 다트 게임의 점수 계산 로직은 아래와 같다.

1. 다트 게임은 총 3번의 기회로 구성된다.
2. 각 기회마다 얻을 수 있는 점수는 0점에서 10점까지이다.
3. 점수와 함께 Single(`S`), Double(`D`), Triple(`T`) 영역이 존재하고 각 영역 당첨 시 점수에서 1제곱, 2제곱, 3제곱 (점수 , 점수 , 점수 )으로 계산된다.
    
    1
    
    2
    
    3
    
4. 옵션으로 스타상(``) , 아차상(`#`)이 존재하며 스타상(``) 당첨 시 해당 점수와 바로 전에 얻은 점수를 각 2배로 만든다. 아차상(`#`) 당첨 시 해당 점수는 마이너스된다.
5. 스타상(``)은 첫 번째 기회에서도 나올 수 있다. 이 경우 첫 번째 스타상(``)의 점수만 2배가 된다. (예제 4번 참고)
6. 스타상(``)의 효과는 다른 스타상(``)의 효과와 중첩될 수 있다. 이 경우 중첩된 스타상(``) 점수는 4배가 된다. (예제 4번 참고)
7. 스타상(``)의 효과는 아차상(`#`)의 효과와 중첩될 수 있다. 이 경우 중첩된 아차상(`#`)의 점수는 -2배가 된다. (예제 5번 참고)
8. Single(`S`), Double(`D`), Triple(`T`)은 점수마다 하나씩 존재한다.
9. 스타상(``), 아차상(`#`)은 점수마다 둘 중 하나만 존재할 수 있으며, 존재하지 않을 수도 있다.

0~10의 정수와 문자 S, D, T, *, #로 구성된 문자열이 입력될 시 총점수를 반환하는 함수를 작성하라.

### 입력형식

---

"점수|보너스|[옵션]"으로 이루어진 문자열 3세트.예)  `1S2D*3T`

- 점수는 0에서 10 사이의 정수이다.
- 보너스는 S, D, T 중 하나이다.
- 옵선은 *이나 # 중 하나이며, 없을 수도 있다.

### 출력형식

---

3번의 기회에서 얻은 점수 합계에 해당하는 정수값을 출력한다.

예) 37

### 입출력 예

---

| 예제 | dartResult | answer | 설명 |
| --- | --- | --- | --- |
| 1 | 1S2D*3T | 37 | 11 * 2 + 22 * 2 + 33 |
| 2 | 1D2S#10S | 9 | 12 + 21 * (-1) + 101 |
| 3 | 1D2S0T | 3 | 12 + 21 + 03 |
| 4 | 1S*2T*3S | 23 | 11 * 2 * 2 + 23 * 2 + 31 |
| 5 | 1D#2S*3S | 5 | 12 * (-1) * 2 + 21 * 2 + 31 |
| 6 | 1T2D3D# | -4 | 13 + 22 + 32 * (-1) |
| 7 | 1D2S3T* | 59 | 12 + 21 * 2 + 33 * 2 |

### 풀이

---

```jsx
function solution(dartResult) {
    var answer = 0;
        //split()을 이용하여 분해하여 배열로
    let dartArr = dartResult.split("");
        //처음 던진 게임 결과
    let score1 = [];
        //점수
    let score2 = [];
        // *의 위치
    let indexOfStar = [];
        // #의 위치 
    let indexOfSh = [];

        //기호들의 위치를 확인
    for (let i = 0; i < dartArr.length; i++) {
      indexOfStar.push(dartArr.indexOf("*", i));
      indexOfSh.push(dartArr.indexOf("#", i));
    }

        // -1의 위치는 현재 없는 것이기 때문에 지워줌 
        // Set()을 이용하여 중복된 숫자 제거
    indexOfStar = [...new Set(indexOfStar)].filter((a) => a != -1);
    indexOfSh = [...new Set(indexOfSh)].filter((a) => a != -1);
    
        // 새게임 시작점
        let start = 0;

        // S,T,D 가 나오면 잘라서 score1 에 push()
    for (let i = 0; i < dartArr.length; i++) {
      if (dartArr[i] == "S" || dartArr[i] == "T" || dartArr[i] == "D") {
        score1.push(dartArr.slice(start, i + 1));
        start = i + 1;
      } else if (dartArr[i] == "#" || dartArr[i] == "*") {
        start += 1;
      }
    }

        //score1[i] 내부에 S,D,T를 확인해서 Math.pow()를 이용하여 계산
        // 정규식 /[^0-9]/g 를 이용하여 숫자가 아닌것을 제거 
    for (let i = 0; i < 3; i++) {
      if (score1[i][score1[i].length -1] == "S") {
        score2.push(score1[i].join().replace(/[^0-9]/g, "") * 1);
      } else if (score1[i][score1[i].length -1] == "D") {
        score2.push(Math.pow(score1[i].join().replace(/[^0-9]/g, ""), 2));
      } else if (score1[i][score1[i].length -1] == "T") {
        score2.push(Math.pow(score1[i].join().replace(/[^0-9]/g, ""), 3));
      }
    }

        // *의 위치에 따라 점수 변경
    for (let i = 0; i < indexOfStar.length; i++) {
      if (2 <= indexOfStar[i] && indexOfStar[i] <= 3) {
        score2[0] = score2[0] * 2;
      } else if (
        4 <= indexOfStar[i] &&
        indexOfStar[i] <= 8 &&
        indexOfStar[i] + 1 != dartArr.length
      ) {
        score2[0] = score2[0] * 2;
        score2[1] = score2[1] * 2;
      } else if (indexOfStar[i] + 1 == dartArr.length) {
        //score2[0] = score2[0] * 2;
        score2[1] = score2[1] * 2;
        score2[2] = score2[2] * 2;
      }
    }

        // #의 위치에 따라 점수 변경
    for (let i = 0; i < indexOfSh.length; i++) {
      if (2 <= indexOfSh[i] && indexOfSh[i] <= 3) {
        score2[0] = score2[0] * -1;
      } else if (
        4 <= indexOfSh[i] &&
        indexOfSh[i] <= 8 &&
        indexOfSh[i] + 1 != dartArr.length
      ) {
        score2[1] = score2[1] * -1;
      } else if (indexOfSh[i] + 1 == dartArr.length) {
        score2[2] = score2[2] * -1;
      }
    }
        // 정답 계산
    for (let i = 0; i < score2.length; i++) {
      answer += score2[i];
    }
    return answer;
}
```
