---
title: Programmers - LV2. 큰 수 만들기
categories: [Programmers]
comments: true
---

[문제](https://programmers.co.kr/learn/courses/30/lessons/42883)

## 접근하기

문자열 `number`와 숫자 `k`가 주어진다. `number`에서 `k`만큼 빼 만들 수 있는 가장 큰 숫자를 만들어 반환한다.

<br>

## 참고 코드

```js
function solution(number, k) {
  let stack = [];

  for (let i = 0; i < number.length; i++) {
    while (k > 0 && stack.length > 0 && stack[stack.length - 1] < number[i]) {
      stack.pop();
      k--;
    }
    stack.push(number[i]);
  }
  stack.splice(stack.length - k, k);
  return stack.join('');
}
```

1. 처음에 이중for문을 이용해서 풀려고 했는데, 잘 안되서 다른 코드를 참고한다.
2. 참고한 코드는 스택을 이용해서 풀었다. 먼저 스택을 하나 정의한다.
3. `number`를 순회하면서, 숫자들을 스택에 푸쉬한다.
4. 푸쉬하다가 스택에 넣은 마지막 숫자와 넣으려는 숫자를 비교해 넣으려는 숫자가 더 클 경우, 기존의 스택에 있던 숫자를 `pop`하고 넣으려는 숫자를 넣게 되면 숫자를 하나 뺸 것이기 때문에 `k` 수를 감소시킨다.
