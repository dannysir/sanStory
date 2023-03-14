---
title: Programmers 코딩테스트 (24)
tags: [Programmers, Coding Test, Lv2, dp]
style: fill
color: light
description: programmers LV2 - 쿼드압축 후 갯수 세기
---

# 2023-02-22 TIL

<br/>
### • 쿼드압축 후 개수 세기
<br/>
### **문제 설명**

---

0과 1로 이루어진 2n x 2n 크기의 2차원 정수 배열 arr이 있습니다. 당신은 이 arr을 [쿼드 트리](https://en.wikipedia.org/wiki/Quadtree)와 같은 방식으로 압축하고자 합니다. 구체적인 방식은 다음과 같습니다.

1. 당신이 압축하고자 하는 특정 영역을 S라고 정의합니다.
2. 만약 S 내부에 있는 모든 수가 같은 값이라면, S를 해당 수 하나로 압축시킵니다.
3. 그렇지 않다면, S를 정확히 4개의 균일한 정사각형 영역(입출력 예를 참고해주시기 바랍니다.)으로 쪼갠 뒤, 각 정사각형 영역에 대해 같은 방식의 압축을 시도합니다.

arr이 매개변수로 주어집니다. 위와 같은 방식으로 arr을 압축했을 때, 배열에 최종적으로 남는 0의 개수와 1의 개수를 배열에 담아서 return 하도록 solution 함수를 완성해주세요.

### 제한 조건

---

- arr의 행의 개수는 1 이상 1024 이하이며, 2의 거듭 제곱수 형태를 하고 있습니다. 즉, arr의 행의 개수는 1, 2, 4, 8, ..., 1024 중 하나입니다.
  - arr의 각 행의 길이는 arr의 행의 개수와 같습니다. 즉, arr은 정사각형 배열입니다.
  - arr의 각 행에 있는 모든 값은 0 또는 1 입니다.

### 입출력 예

---

| arr                                                                                                                                               | result  |
| ------------------------------------------------------------------------------------------------------------------------------------------------- | ------- |
| [[1,1,0,0],[1,0,0,0],[1,0,0,1],[1,1,1,1]]                                                                                                         | [4,9]   |
| [[1,1,1,1,1,1,1,1],[0,1,1,1,1,1,1,1],[0,0,0,0,1,1,1,1],[0,1,0,0,1,1,1,1],[0,0,0,0,0,0,1,1],[0,0,0,0,0,0,0,1],[0,0,0,0,1,0,0,1],[0,0,0,0,1,1,1,1]] | [10,15] |

### 입출력 예 설명

입출력 예 #1

- 다음 그림은 주어진 arr을 압축하는 과정을 나타낸 것입니다.
- ![https://grepp-programmers.s3.ap-northeast-2.amazonaws.com/files/production/d6900862-8be4-4610-aaef-bc8efd5650cf/ex1.png](https://grepp-programmers.s3.ap-northeast-2.amazonaws.com/files/production/d6900862-8be4-4610-aaef-bc8efd5650cf/ex1.png)
- 최종 압축 결과에 0이 4개, 1이 9개 있으므로, `[4,9]`를 return 해야 합니다.

입출력 예 #2

- 다음 그림은 주어진 arr을 압축하는 과정을 나타낸 것입니다.
- ![https://grepp-programmers.s3.ap-northeast-2.amazonaws.com/files/production/952a05b7-5157-4211-82d9-02845c187e13/ex2.png](https://grepp-programmers.s3.ap-northeast-2.amazonaws.com/files/production/952a05b7-5157-4211-82d9-02845c187e13/ex2.png)
- 최종 압축 결과에 0이 10개, 1이 15개 있으므로, `[10,15]`를 return 해야 합니다.

### 풀이 과정

---

- 왼쪽 가장 위를 (0,0) 으로 생각하고 전체 길이 r에서 r/2 만큼 계속 잘라준다.
- 자른 후에 안에 있는 원소를 확인 후에 전부 동일한 숫자라면 answer에 반영
- 십자가로 자르면 4개의 영역으로 나누어지기 때문에 각 영역을 재귀를 이용하여 계산

### 풀이

---

```jsx
function solution(arr) {
  answer = [0, 0];
  //쿼드 압축 함수
  function SanE(x, y, r) {
    // 만약 길이가 1이면 쿼드 압축 종료
    if (r === 1) return answer[arr[x][y]]++;
    let flag = true;
    // 분할한 부분의 원소가 전부 같은지 확인
    for (let i = x; i < x + r; i++) {
      for (let j = y; j < y + r; j++) {
        if (arr[i][j] !== arr[x][y]) {
          flag = false;
          break;
        }
      }
    }
    // 만약 원소가 모두 같거나 r이 1이면 answer 에 값 입력
    if (flag) return answer[arr[x][y]]++;

    // flag가 false 이면 분할 진행
    r /= 2;

    // 재귀를 이용하여 십자가로 자른 나머지 부분도 계산
    SanE(x, y, r);
    SanE(x + r, y, r);
    SanE(x, y + r, r);
    SanE(x + r, y + r, r);
  }
  SanE(0, 0, arr.length);
  return answer;
}
```
