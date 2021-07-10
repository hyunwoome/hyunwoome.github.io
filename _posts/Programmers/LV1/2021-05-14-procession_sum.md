---
title: Programmers - LV1. 행렬의 덧셈
categories: [Programmers]
comments: true
---

[문제](https://programmers.co.kr/learn/courses/30/lessons/12950)

## 접근하기

주어진 2차원 배열 두개를 같은 행과 열의 요소를 더해서 2차원 배열로 반환하는 문제이다.

<br>

## 내 풀이

```js
function solution(arr1, arr2) {
  var answer = [];
  for (let i = 0; i < arr1.length; i++) {
    let arr = [];
    for (let j = 0; j < arr1[i].length; j++) {
      arr.push(arr1[i][j] + arr2[i][j]);
    }
    answer.push(arr);
  }
  return answer;
}
```

1. 이중for문을 사용해서 각 열과 행을 더한 후 반환한다.
