---
title: Programmers - LV1. 제일 작은 수 제거하기
categories: [Programmers]
comments: true
---

[문제](https://programmers.co.kr/learn/courses/30/lessons/12935)

## 접근하기

주어진 배열에서 제일 작은수를 가진 원소만 제거 후 반환한다. 만약 배열의 원소 개수가 1개뿐이라면 바로 -1을 반환한다.

<br>

## 내 코드

```js
function solution(arr) {
  if (arr.length !== 1) {
    let minIdx = arr.indexOf(Math.min(...arr));
    arr.splice(minIdx, 1);
    return arr;
  } else {
    return [-1];
  }
}
```

1. 배열의 길이가 1개라면 바로 `[-1]`을 반환한다.
2. 그렇지 않다면, 배열의 최소값과 동시에 인덱스를 찾고,
3. `splice()`를 사용해 배열을 제거한 후 제거된 원래 배열을 반환한다.
