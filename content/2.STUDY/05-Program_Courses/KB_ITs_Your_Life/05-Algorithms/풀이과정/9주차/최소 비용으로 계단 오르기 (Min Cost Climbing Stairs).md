---
tags:
  - 프로그래머스
  - leetcode
link: https://campus.programmers.co.kr/tryouts/146285/challenges
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
cost = 각 단계에서 지불해야하는 비용 담겨있는 int 배열

배열의 인덱스는 해당 인덱스 번째 단계를 의미

0번째 또는 1번째 단계에서 시작 가능하며, 한 번에 한 계단 또는 두 계단 올라갈 수 있음

계단 꼭대기에 도달하기 위한 최소 비용 return
#### 접근 방법
계단 꼭대기 = 배열의 크기?

`cost = [10, 15, 20]`인 경우
0번째에서 시작한다면
- 한 계단 + 한 계단 + 한 계단 → 10 + 15 + 20 = 45
- 한 계단 + 두 계단 → 10 + 20 = 30
- 두 계단 + 한 계단 → 20

1번째에서 시작한다면
- 한 계단 + 한 계단 → 15 + 20 = 35
- 두 계단 → 15
⇒ 최소 비용은 15

오전에 풀었던 [[계단 오르기 (Climbing Stairs)]] 문제의 확장 버전

계단 오르기 문제는 DP 이용해서 n까지 올라간다면 n-1과 n-2에서 오르는 경우를 구하는 작은 문제로 잘라서 실행하고, 각 계단에서 올라갈 수 있는 가짓수를 memoization했었다.

이번 문제는 n-1과 n-2에서 올라가는 과정에서 n-1에서 출발하는 경우의 비용 값과 n-2에서 출발하는 경우의 비용을 비교해서 최소인 값을 memoization에 저장하고, 이를 반복하여 최솟값을 return 하면 되지 않을까….?
→ 구현을 못함… 🥹

---

수업 중 해설 → 떠올린 로직과 비슷한 듯…???
#### 코드 구현
```java
// 구현 시도 코드
import java.util.*;
class Solution {
    Map<Integer, Integer> memo = new HashMap<>();
    public int solution(int[] cost) {
        int n = cost.length; // 꼭대기층
        dp(cost, n);
        int answer = 0;
        return answer;
    }
    
    int dp(int[] cost, int n) {
        if (n == 0) return cost[n];
        if (n == 1) return cost[n];
        
        if (!memo.containsKey(n)) {
            memo.put(n, dp(cost, cost[n - 1]) + dp(cost, cost[n - 2]));
        }
        System.out.println(memo);
        return Math.min(dp(cost, cost[n - 1]), dp(cost, cost[n - 2]));
    }
}
```

```java
// 해설 - 완전탐색 구현 코드(정확성 통과, 효율성 실패)
import java.util.*;
class Solution {
    public int solution(int[] cost) {
        int n = cost.length; // 꼭대기층
        int answer = dp(cost, n);
        return answer;
    }
    
    int dp(int[] cost, int n) {
        if (n == 0 || n == 1) return 0;
        
        return Math.min(dp(cost, n - 1) + cost[n - 1], dp(cost, n - 2) + cost[n - 2]);
    }
}
```

```java
// 해설 - DP 구현 코드(Top-down 방식)
import java.util.*;
class Solution {
    public int solution(int[] cost) {
        int n = cost.length; // 꼭대기층
        int[] memo = new int[n + 1];
        Arrays.fill(memo, -1);
    
        int answer = dp(cost, n, memo);
        return answer;
    }
    
    int dp(int[] cost, int n, int[] memo) {
        if (n == 0 || n == 1) return 0;
        
        if (memo[n] == -1) {
            memo[n] = Math.min(dp(cost, n - 1, memo) + cost[n - 1], dp(cost, n - 2, memo) + cost[n - 2]);
        }
        
        return memo[n];
    }
}
```

```java
// 해설 - DP 구현 코드(Bottom-up 방식)
import java.util.*;
class Solution {
    public int solution(int[] cost) {
        int n = cost.length; // 꼭대기층
        int[] memo = new int[n + 1];
        Arrays.fill(memo, -1);
        
        memo[0] = 0;
        memo[1] = 0;        
        for (int i = 2; i <= n; i++) {
            memo[i] = Math.min(memo[i - 1] + cost[i - 1], memo[i - 2] + cost[i - 2]);
        }
        
        int answer = memo[n];        
        return answer;
    }
}
```

#### 배우게 된 점
처음부터 DP로 구현하려고 하지 말고 **일단 완전탐색으로 구현한 뒤 DP로 바꿔서 구현**해야 그나마 풀 수 있다…

DP 문제라고 알고 있으니까 처음부터 DP 적용하려고 하는 것 → 실제 시험에서는 DP 문제라고 안 알려줌
