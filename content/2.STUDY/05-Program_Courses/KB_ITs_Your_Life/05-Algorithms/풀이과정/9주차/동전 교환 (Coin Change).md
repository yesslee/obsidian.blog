---
tags:
  - 프로그래머스
  - leetcode
link: https://campus.programmers.co.kr/tryouts/146284/challenges
weeks: 9
type: 실습
category:
  - DP
status: Solved
solution_type:
  - 정답(답안 참고)
  - 오답(스스로 풀이)
---
#### 문제파악
4주차의 [[2.STUDY/05-Program_Courses/KB_ITs_Your_Life/05-Algorithms/풀이과정/4주차/Coin Change|Coin Change]] 문제와 동일한 문제!
#### 접근 방법
이전에는 BFS를 통해서 구현했으나, DP로 구현해보기!

##### Top-down 방식
**Base case**
- `amount == 0`: 금액이 0이면 동전 필요 X → return 0
- `amount < 0`: 금액이 음수라면 유효하지 않은 경우 → `Integer.MAX_VALUE`를 반환하여 무시

**Memoization**
- 계산된 `amount` 가 `memo` 에 들어있으면 재귀호출 대신 해당 값을 가져다가 사용

**필요한 최소 동전 개수 계산하기**
- `coins` 배열의 각 동전에 대해, 현재 `amount`에서 해당 동전의 값을 뺀 결과(`amount - coin`)로 `dp` 메서드를 재귀 호출
- 반환된 값이 `Integer.MAX_VALUE`가 아니면, 그 결과에 1을 더하여 현재 동전을 사용 개수를 기록!

##### Bottom-up 방식
금액이 1인 동전부터 amount 금액에 해당하는 동전이 존재한다고 가정 → 배열의 인덱스
필요한 최소 동전의 수를 반환해야하므로, 큰 값으로 초기화해서 배열 생성

1부터 amount 까지 각 금액에 대해 각 동전 개수를 확인하면서 `i - coin`이 양수면 현재 값과 `dp[i - coin] + 1`을 비교하여 최소값으로 `dp[i]`를 업데이트
→ `i - coin`을 만드는 데 필요한 최소 동전 갯수를 안다면 동전을 하나 더 추가하여 `i`를 만들 수 있기 때문!

`dp[amount]`가 `amount`보다 크다면, 주어진 동전으로 amount 값을 만들 수 없다는 뜻이므로 return -1
#### 코드 구현
```java
// Top-down 방식
import java.util.*;
class Solution {
    public int solution(int[] coins, int amount) {
        Map<Integer, Integer> memo = new HashMap<>();
        int answer = dp(coins, amount, memo);
        if (answer == Integer.MAX_VALUE) return -1;
        
        return answer;
    }
    
    int dp(int[] coins, int amount, Map<Integer, Integer> memo) {
        if (amount == 0) return 0;
        if (amount < 0) return Integer.MAX_VALUE;
        
        if (memo.containsKey(amount)) return memo.get(amount);

        int min = Integer.MAX_VALUE;

        for (int coin : coins) {
            int result = dp(coins, amount - coin, memo);
            if (result != Integer.MAX_VALUE) {
                min = Math.min(min, result + 1);
            }
        }

        memo.put(amount, min);
        return min;
    }
}
```

```java
// Bottom-up 방식
import java.util.*;
class Solution {
    public int solution(int[] coins, int amount) {
        int[] dp = new int[amount + 1];
        for (int i = 1; i <= amount; i++) dp[i] = amount + 1;
				// import java.util.*; 하고 Arrays.fill(dp, amount + 1); 사용하면 조금 더 간단하게 초기화 가능!
        
        dp[0] = 0;
        
        for (int i = 1; i <= amount; i++) {
            for (int coin : coins) {
                if (0 <= i - coin) dp[i] = Math.min(dp[i], dp[i - coin] + 1);
            }
        }
        
        if (dp[amount] > amount) return -1;
        
        return dp[amount];
    }
}
```

#### 배우게 된 점