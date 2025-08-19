---
tags:
  - leetcode
link: https://leetcode.com/problems/coin-change/description/
weeks: 4
type: 예제
category:
  - 그래프
  - BFS
  - DP
status: Not Started
solution_type:
---
#### 문제파악
amount 값과 coins 배열이 주어질 때 amonut 값을 동전 갯수 **최소한의 개수** 로 맞춰야 함
#### 접근 방법
액수 큰 동전부터 값 채우면 되지 않을까? NOPE

`amount = 6`, `coins = [1, 3, 4]`

`6 = 4 + 1 + 1` → (3)
`6 = 3 + 3` → (2)

최소갯수 2개

인접한 곳으로 이동하며 탐색하여 최소 횟수 구하는 문제 → BFS

모든 케이스 돌아보고 그 중에서 동전 개수 적게 쓴 경우를 판별해야함 → 모든 경우 전부 확인해야함(나랑 가까운 곳부터 방문하는 bfs 특징)????
#### 코드 구현
```java
import java.util.ArrayDeque;
import java.util.Queue;

class Solution {
    public int coinChange(int[] coins, int amount) {
        if (amount == 0) return 0;

        Queue<int[]> queue = new ArrayDeque<>();
        boolean[] visited = new boolean[amount + 1];
        queue.add(new int[] {amount, 0});
        
        while (!queue.isEmpty()) {
            int[] cur = queue.remove();
            int currentAmount = cur[0];
            int currentCount = cur[1];
            
            for (int i = 0; i < coins.length; i++) {
                int nextAmount = currentAmount - coins[i];
                if (nextAmount == 0) {
                    return currentCount + 1;
                } else if (nextAmount > 0 && !visited[nextAmount]) {
                    queue.add(new int[] {nextAmount, currentCount + 1});
                    visited[nextAmount] = true;
                }
            }
        }
        
        return -1;
    }
}
```

#### 배우게 된 점
중요한 문제
BFS와 DFS의 차이점 드러나는 문제