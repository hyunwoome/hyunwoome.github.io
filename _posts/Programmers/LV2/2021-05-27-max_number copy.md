---
title: LV2. 위장
categories: [Programmers]
comments: true
---

[문제](https://programmers.co.kr/learn/courses/30/lessons/42578#qna)

## 접근하기

문자열 배열로 이루어진 2차원 배열 `clothes`가 주어진다. 각 배열은 [의상의 이름, 의상의 종류]를 나타내며, 서로 다른 옷의 조합의 수를 반환하는 문제이다.

<br>

## 참고 코드

```js
function solution(clothes) {
  let answer = 1;
  const hash = {};
  for (let i = 0; i < clothes.length; i++) {
    hash[clothes[i][1]] = (hash[clothes[i][1]] || 1) + 1;
  }
  for (const key in hash) {
    answer *= hash[key];
  }
  return answer - 1;
}
```

1. 처음에 각 카테고리별로 중복된 수를 구해서 `{headgear: 2, eyewear: 1}` 처럼 구하고 곱한 후 `clothes`의 길이를 더한 수를 반환했는데 실행할 때 다 대부분 틀렸고, 다른 코드를 참고하여 풀게 되었다.
2. 처음 hash를 구할 때, 내가 구했던 것과 다르게, 참고 코드에선 초기값을 1을 주고 시작해서 `{headgear: 3, eyewear: 2}` 이런식으로 나왔다. 이런식으로 한 이유는, 상의와 하의, 신발을 모두 갖춰입을 필요가 없어서 기존 카테고리의 중복된 수 + 1을 해준다.
3. 해당 카테고리 수를 곱하고, 마지막에 -1을 해주는데 모든 의상을 입지 않는 경우는 없으므로 -1을 해준다.
