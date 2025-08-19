---
tags:
  - 프로그래머스
  - leetcode
link: https://campus.programmers.co.kr/tryouts/146282/challenges
weeks: 9
type: 예제
category:
  - DP
status: Solved
solution_type:
  - 정답(답안 참고)
  - 오답(스스로 풀이)
---
#### 문제파악
n = 올라야하는 계단의 수

매번 1계단 또는 2계단을 오를 수 있다

꼭대기까지 올라가는데 몇 가지 서로 다른 방법이 존재하는지 구하기
#### 접근 방법
아예 감을 못잡았다…. 뭔가 이전 값을 이용하면 될 것 같은 느낌은 있었는데, 어떻게 활용해야할지 감을 못 잡았다.


**수업 중 해설**

n까지 가는 방법 = n-2에서 오는 방법(2계단 이동) + n-1에서 오는 방법(1계단 이동)
→ 알고보니 피보나치와 거의 동일한 문제였다…

```java
Map<Integer, Integer> memo = new HashMap<>();
int cs(int n) {
	 if (n == 1) return 1;
	 if (n == 2) return 2;
	 
	 if (!memo.containsKey(n)) {
		 memo.put(n, cs(n - 1) + cs(n - 2);
	 }
	 
	 return memo.get(n);
}
```
#### 코드 구현
```java
// Top-down 방식
import java.util.*;
class Solution {
    Map<Integer, Integer> memo = new HashMap<>();
    public int solution(int n) {        
        return dp(n);
    }
    
    int dp(int n) {
        if (n == 1) return 1;
        if (n == 2) return 2;
        
        if (!memo.containsKey(n)) {
            memo.put(n, dp(n - 1) + dp(n - 2));
        }
        
        return memo.get(n);
    }
}
// 효율성 통과가 안된다...(코드 문제는 아니라고 하심)
```

```java
// Bottom-up 방식
class Solution {
    public int solution(int n) {
        int[] dp = new int[n + 1];
        dp[1] = 1;
        dp[2] = 2;
        
        for (int i = 3; i <= n; i++) {
            dp[i] = dp[i - 1] + dp[i - 2];
        }
        
        return dp[n];
    }
}
```

#### 배우게 된 점