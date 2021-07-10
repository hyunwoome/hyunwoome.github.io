---
title: Programmers - LV2. 행렬의 곱셈
categories: [Programmers]
comments: true
---

[문제](https://programmers.co.kr/learn/courses/30/lessons/12949)

## 접근하기

두 개의 2차원 정수형 배열이 주어진다. 두 개의 배열을 곱해서 반환한다.

<br>

## 내 코드

```js
function solution(arr1, arr2) {
  const main_length = arr1.length; // 3
  const arr1_length = arr1[0].length; // 2
  const arr2_length = arr2[0].length; // 2

  let answer = Array(main_length);
  for (let m = 0; m < main_length; m++) {
    answer[m] = Array(arr2_length).fill(0);
    for (let t = 0; t < arr2_length; t++) {
      for (let o = 0; o < arr1_length; o++) {
        answer[m][t] += arr1[m][o] * arr2[o][t];
      }
    }
  }
  return answer;
}
```

1. 행렬을 곱하려면, 먼저 각 배열을 몇 번 순회해야 하는지 파악해야 한다.
2. 먼저 해당 문제의 첫 번째 입출력 결과를 보면 3행이다. 이 것은 전체적으로 3번 순회한다는 의미로 배열 `arr1`의 원소만큼 돌면 되기 때문에 개수를 뽑아놓는다.

```js
const main_length = arr1.length; // 3
```

3. 이제 배열의 내부를 돌 차례이다. `arr1`배열의 내부의 원소 개수를 구하고, `arr2`배열의 원소 개수를 구한다.

```js
const arr1_length = arr1[0].length; // 2
const arr2_length = arr2[0].length; // 2
```

4. 이제 원소 `main_length`개를 담을 수 있는 배열을 만든다.
5. `main_length`만큼 순회를 하며, 각 원소에 `arr2_length`만큼 0을 채운다.

```js
let answer = Array(main_length);
for (let m = 0; m < main_length; m++) {
  answer[m] = Array(arr2_length).fill(0);
}

// [
//  [0, 0]
//  [0, 0]
//  [0, 0]
// ]
```

6. 위에서 만든 2차원 배열에 값을 채워넣자.
7. 이중for문을 사용해서 `answer`배열에 행렬의 곱셈을 더한다.
