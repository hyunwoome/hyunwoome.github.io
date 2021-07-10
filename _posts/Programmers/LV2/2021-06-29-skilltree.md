---
title: Programmers - LV2. 스킬트리
categories: [Programmers]
comments: true
---

[문제](https://programmers.co.kr/learn/courses/30/lessons/49993)

## 문제 설명

문자열 `skill`과 문자열 배열 `skill_trees`가 주어진다.
문제는 꽤 길지만, 결국 묻고자 하는 것은, `skill`의 문자열 순서와 일치하는 `skill_trees`의 문자열을 찾아 그 갯수를 반환하는 문제이다.
예를 들어, `skill`이 `CBD`라고 한다면, `D`가 올려면 반드시 `B`가 앞에 있어야 하고, `B`가 오려면 반드시 `C`가 있어야 한다. 이 순서만 지킨다면 가운데 어떠한 문자가 들어와도 상관없다.

**예시 1**

```
skill: "CBD"
skill_trees: ["BACDE", "CBADF", "AECB", "BDA"]
return: 2
- "BACDE": B가 오기전에 C가 먼저 와야하므로 잘못된 문자열이다.
- "CBADF": 가능하다.
- "AECB": 가능하다.
- "BDA": B가 오기전에 C가 먼저 와야하므로 잘못된 문자열이다.
```

<br>

## 해결방법

**접근하기**

주어진 `skill`의 문자열 순서와 비교해야 하므로 정렬을 할 순 없다.
먼저 `tree_skills`의 각 문자열에 `skill`의 **문자가 들어가 있는지 먼저 확인**하고, 들어있다면 이제 **순서**를 비교해야 한다.

**알고리즘**

1. `skill_trees`는 문자열 배열로 이루어져 있다. 그러므로 배열 안의 문자열에 접근하기 위해 이중for문을 사용할 것이다.
2. for문안에 `skill_trees`의 각 문자열이 `skill`과 순서가 일치하는지 참, 거짓으로 파악하기 위해 `isPossible`이란 변수를 정의한다.
3. `idx`는 `skill`의 순서를 추적하기 위한 변수이다.
4. 다음 for문에서 실질적으로 각 문자열의 문자들이 `skill`에 포함되어 있는지 판별하는 부분이다.
5. `skill.includes(skill_trees[i][j])`코드는 `skill`문자열 내부에 `skill_trees`배열의 문자열의 문자가 속해있는지 확인하고, 속해있다면 다음 if문에 순서를 확인한다.
6. `skill`에 포함되어 있는 문자 `skill_trees[i][j]`가 `skill[idx]`, 즉 `skill`문자열의 문자와 동일하다면 `idx`를 증가시켜 다음 순서도 맞는지 확인한다. `tree_skills`의 개별 문자열이 이 순서와 일치하다면 문제에서 요구하는 조건에 부합하는 문자열이므로 `count`를 증가시킨다.
7. if문에서 하나라도 다르다면, `isPossible`은 `false`가 되고 `count`가 증가되지 않을 것이다.

<br>

## 풀이코드

```js
function solution(skill, skill_trees) {
  let count = 0;

  for (let i = 0; i < skill_trees.length; i++) {
    let isPossible = true;
    let idx = 0;

    for (let j = 0; j < skill_trees[i].length; j++) {
      if (skill.includes(skill_trees[i][j])) {
        if (skill_trees[i][j] === skill[idx]) {
          idx++;
        } else {
          isPossible = false;
          break;
        }
      }
    }
    if (isPossible) count++;
  }
  return count;
}
```
