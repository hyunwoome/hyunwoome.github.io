---
title: Solve Tree Problems Recursively
categories: [Algorithm]
comments: true
---

[참고](https://leetcode.com/explore/learn/card/data-structure-tree/17/solve-problems-recursively/534/)

## 재귀적으로 트리 문제 해결

**재귀**(Recursion)는 트리 문제를 해결하기 위한 가장 강력하고 빈번하게 사용되는 기술 중 하나이다.

우리가 알고 있듯이, 트리는 값과 자식 노드에 대한 참조 리스트를 포함하는 노드(루트 노드)로 재귀적으로 정의할 수 있다. 재귀는 트리의 아주 자연스러운 특징 중 하나이다. 그러므로, 많은 트리 문제들은 재귀적으로 해결될 수 있다. 각각의 재귀 함수 호출에 대해 현재 노드의 문제에만 초점을 맞추며 하위 노드의 문제를 해결하기 위해 함수를 재귀적으로 호출한다.

일반적으로, **위에서 아래로 접근하는 하향식 방식**(top-down) 또는 **밑에서 위로 접근하는 상향식 방식**(bottom-up)을 사용해서 트리문제를 재귀적으로 해결할 수 있다.

<br>

## Top-down식 해결 방법

"Top-down"방식은 각 재귀 호출에서, 먼저 노드를 방문하여 몇가지 값을 찾고 함수를 재귀적으로 호출할 때 이 값을 자식 노드에게 전달한다. 그래서 "Top-down"방식 해결법은 **전위 순회**(pre-order)와 같은 문제를 해결할 때 고려할 수 있다. 구체적으로 재귀 함수 `top_down(root, params)`은 다음과 같이 동작한다.

```
1. return specific value for null node
2. update the answer if needed                      // answer <-- params
3. left_ans = top_down(root.left, left_params)      // left_params <-- root.val, params
4. right_ans = top_down(root.right, right_params)   // right_params <-- root.val, params
5. return the answer if needed                      // answer <-- left_ans, right_ans
```

예를들면, 다음과 같은 문제에 고려할 수 있다 : **이진 트리가 주어지면 최대 깊이를 찾는 문제**

알다시피 루트 노드의 깊이는 `1`이다. 각각의 노드에 대해서 깊이를 안다면, 하위 노드의 깊이를 알 수 있을 것이다. 그러므로, 만약 함수를 재귀적으로 호출 할 때 매개변수로서 노드의 깊이를 전달하면 모든 노드들은 그 깊이를 알 수 있을 것이다. 리프 노드에 대해선(자식이 없는 노드, 마지막 노드) 그 깊이를 사용하여 최종 답변을 업데이트 할 수 있다. 다음은 재귀함수 `maximum_depth (root, depth)`에 대한 의사 코드이다.

```
1. return if root is null
2. if root is a leaf node:
3.     answer = max(answer, depth)         // 필요한 경우 answer를 갱신
4. maximum_depth(root.left, depth + 1)     // 왼쪽 자식 노드에 대해 재귀적으로 함수를 호출
5. maximum_depth(root.right, depth + 1)    // 오른쪽 자식 노드에 대해 재귀적으로 함수를 호출
```

즉, 리프 노드까지 도착하면, 더 이상 자식 노드는 없기 때문에 깊이에 대한 답을 갱신한다. 이 과정을 트리의 줄기마다 반복한다.

```js
const maximum_depth = (root, depth) => {
  if (!root) return;

  if (root.left === null && root.right === null) {
    answer = Math.max(answer, depth);
  }
  maximum_depth(root.left, depth + 1);
  maximum_depth(root.right, depth + 1);
};
```

<br>

## Bottom-up식 해결 방법

"Bottom-up"은 또 다른 재귀 해결방법이다. 각각의 재귀 호출에서, 첫 번째로 모든 하위 노드를 재귀적으로 함수를 호출하고, 그런 다음 반환된 값과 현재 노드 자체의 값에 따라 답을 얻는다. 이러한 절차는 **후위 순회**(post-order)를 해야하는 문제에 대해 고려할 수 있다. 일반적인 "bottom-up"방식의 재귀 함수 `bottom_up(root)`는 다음과 같다.

```
1. return specific value for null node
2. left_ans = bottom_up(root.left)      // 왼쪽 자식에 대한 함수를 재귀적으로 호출
3. right_ans = bottom_up(root.right)    // 오른쪽 자식에 대한 함수를 재귀적으로 호출
4. return answers                       // answer <-- left_ans, right_ans, root.val
```

이제 최대 깊이 문제에 대해 기존과 다른 방식으로 생각해보자.

만약 왼쪽 자식 하위 트리의 최대 깊이 `l`과 오른쪽 자식 하위 트리의 최대 깊이 `r`을 알고 있다면 이 문제를 풀 수 있다. 우리는 `l`과 `r`사이의 최대 값을 선택하고 1을 더해 현재 노드에 하위 트리의 최대 깊이를 얻을 수 있다. 즉, `x = max(l, r) + 1`이다.

이 것은 각 노드에 대해서 자식에 대한 문제를 해결한 후에 답을 얻을 수 있다는 것을 의미한다. 따라서, "bottom-up" 방식의 해결 방법을 사용하여 이 문제를 해결할 수 있다.

다음은 재귀 함수 maximum_depth (root)에 대한 의사 코드이다.

```
1. return 0 if root is null                 // 노드가 null이라면 0을 반환한다.
2. left_depth = maximum_depth(root.left)
3. right_depth = maximum_depth(root.right)
4. return max(left_depth, right_depth) + 1  // 하위트리에 있는 루트의 깊이를 반환한다.
```

```js
const maximum_depth = (root) => {
  if (!root) return;

  let leftDepth = maximum_depth(root.left);
  let rightDepth = maximum_depth(root.right);
  return Math.max(leftDepth, rightDepth);
};
```

<br>

## 결론

재귀를 이해하고 문제에 대한 재귀 해결 방법을 찾는 것은 쉽지 않다. 충분한 연습이 필요하다.

트리 문제를 만났을 때, 우리 자신에게 두 가지 질문을 해보자.
노드가 답을 알 수 있도록 몇 가지 매개 변수를 결정할 수 있을까?
이 매개 변수와 노드 자체의 값을 사용하여 자식에게 전달 할 매개 변수를 결정할 수 있을까?
만약 두 질문 다 대답이 **예**라면, 이 문제를 `"top-down"` 방식의 재귀를 사용해서 해결해보자.

또는 이렇게도 생각할 수 있을 것이다.
트리의 노드에 대해 자식의 답을 알고 있다면 해당 노드의 답을 계산할 수 있을까?
만약 질문에 대답이 **예**라면 `"bottom-down"`방식으로 접근하여 문제를 해결해 보자.
