---
tags:
  - leetcode
link: 
weeks: 3
type: 예제
category:
  - 순열조합
  - 완전탐색
status: Solved
solution_type:
  - 정답(답안 참고)
---
#### 문제파악
1 ~ n까지의 정수 중 k개를 선택해서 만들 수 있는 모든 조합 구하기
#### 접근 방법
조합 = 순서 고려 X = 배열에 들어있는 숫자가 같으면 같은 조합

`n = 4` 이고 `k = 2` 일 때 만들 수 있는 모든 조합은
`[[1,2],[1,3],[1,4],[2,3],[2,4],[3,4]]`
→ `[1, 2]` 와 `[2, 1]` 은 같은 조합으로 취급된다


1부터 n까지 순회하면서 조합 배열에 현재 숫자를 추가한다

추가한 숫자는 이후에 확인할 필요가 없으므로 그 다음 숫자부터 n까지 순회하며 조합 배열에 요소를 추가한다

요소를 추가하면서 조합 배열의 길이가 k와 같아지면 완성된 배열을 넣는 리스트에 추가

![[IMG_0217.jpeg|백트래킹 동작 구조 이해하기 위해 그린 그림]]
#### 코드 구현
```java
class Solution {
		// 완성된 순열을 넣는 리스트는 전역변수로 설정
    List<List<Integer>> result = new ArrayList<>();
    public List<List<Integer>> combine(int n, int k) {
        backtrack(1, n, k, new ArrayList<>());
        
        return result;
    }

		// 백트래킹 진행할 재귀함수
    void backtrack(int start, int n, int k, List<Integer> combi) {
        // base case
        if (combi.size() == k) { // 조합 만드는 배열의 길이가 k와 같아지는 시점이 하나의 조합이 완성된 시점
            result.add(new ArrayList<>(combi)); // 완성된 하나의 조합을 결과 출력할 리스트에 추가
            return;
        }

        // recursive call
        for (int i = start; i <= n; i++) {
            combi.add(i);
            backtrack(i + 1, n, k, combi);
            combi.remove(combi.size() - 1);
        }
    }
}
```

#### 배우게 된 점
[[2.STUDY/05-Program_Courses/KB_ITs_Your_Life/05-Algorithms/풀이과정/3주차/Permutations|Permutations]] 처럼 n을 가지고 1~n이 들어있는 배열을 만들어서 해결하려고 했는데 굳이 이런 식으로 배열을 만들지 않아도 풀 수 있는 문제였다….