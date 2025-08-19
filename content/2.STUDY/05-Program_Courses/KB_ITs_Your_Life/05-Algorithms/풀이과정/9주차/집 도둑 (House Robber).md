---
tags:
  - 프로그래머스
  - leetcode
link: https://campus.programmers.co.kr/tryouts/146286/challenges
weeks: 9
type: 실습
category:
  - DP
status: In Progress
solution_type:
  - 정답(답안 참고)
  - 오답(스스로 풀이)
---
#### 문제파악
nums = 각 집마다 숨겨진 돈의 금액을 담고있는 배열
→ 인접한 값은 경찰에게 신고당하기 때문에 가져올 수 없다

최대로 털 수 있는 금액 return
#### 접근 방법
맨 처음 터는 집은 첫 번째 집 또는 두 번째 집을 턴다

처음 턴 집을 기준으로 옆집을 털었을 경우의 금액을 기록해두고, 더 큰 값이면 해당 집을 터는걸로 변경, 하나 건너뛰고 다시 털어보기 시작

현재 값보다 작은 값인 경우, 현재 값을 확정시키며, 해당 집을 털은 것이므로 하나 건너뛰고 그 다음 집부터 다시 누적금액 확인?

---

`i = max(i - 1 vs i - 2 + i)`

`dp[i] = max(dp(i - 1), dp(i - 2) + nums[i])`
#### 코드 구현
```java
// 수업 중 해설 코드 - 완전탐색
class Solution {
    public int solution(int[] nums) {
        int n = nums.length;
        return dp(nums, n - 1);
    }
    
    public int dp(int[] nums, int n) {
        if (n == 0) return nums[0];
        if (n == 1) return Math.max(nums[0], nums[1]);
        
        return Math.max(dp(nums, n - 1), dp(nums, n - 2) + nums[n]);
    }
}
```

```java
// 수업 중 해설 코드 - 완전탐색 → DP(Top-down)
import java.util.*;
class Solution {
    public int solution(int[] nums) {
        int n = nums.length;
        int[] memo = new int[nums.length];
        Arrays.fill(memo, -1);
        
        return dp(nums, n - 1, memo);
    }
    
    public int dp(int[] nums, int n, int[] memo) {
        if (n == 0) return nums[0];
        if (n == 1) return Math.max(nums[0], nums[1]);
        
        if (memo[n] == -1) {
            memo[n] = Math.max(dp(nums, n - 1, memo), dp(nums, n - 2, memo) + nums[n]);
        }
        
        return memo[n];
    }
}
```

```java
// 수업 중 해설 코드 - 완전탐색 → DP(Bottom-up)
import java.util.*;
class Solution {
    public int solution(int[] nums) {
        int n = nums.length;
        int[] dp = new int[n];
        
        dp[0] = nums[0];
        dp[1] = Math.max(nums[0], nums[1]);
        for (int i = 2; i < n; i++) {
            dp[i] = Math.max(dp[i - 1], dp[i - 2] + nums[i]);
        }
        
        return dp[n - 1];
    }
}
```
#### 배우게 된 점