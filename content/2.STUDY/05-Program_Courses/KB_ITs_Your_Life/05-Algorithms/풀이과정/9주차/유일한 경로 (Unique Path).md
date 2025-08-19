---
tags:
  - 프로그래머스
  - leetcode
link: https://campus.programmers.co.kr/tryouts/146283/challenges
weeks: 9
type: 예제
category:
  - DP
status: In Progress
solution_type:
  - 정답(답안 참고)
  - 오답(스스로 풀이)
---
#### 문제파악
m x n 격자의 (0, 0) 위치에 로봇이 있고, (m-1, n-1) 위치로 이동하려고 할 때 도달 가능한 모든 고유 경로의 수 return

로봇은 오른쪽 또는 아래쪽으로만 한 칸씩 이동 가능
#### 접근 방법
가장 쉽게 푸는 방법 = 조합으로 푸는 방법
#### 코드 구현
```java
// 구현 시도 코드
class Solution {
    public int solution(int m, int n) {
        int answer = 0;
        int[][] memo = new int[m + 1][n + 1];
        
        dp(m, n, memo);
        
        return answer;
    }
    
    int dp(int m, int n, int[][] memo) {
        if (m == 0 && n == 0) return 0;
        if (m == 0 || n == 0) return 1;
        if (m == 1 && n == 1) return 2;
        
        for (int r = 1; r < m; r++) {
            for (int c = 1; c < n; c++) {
                memo[r][c] = dp(r - 1, c, memo) + dp(r, c - 1, memo);
            }
        }
        for (int[] x : memo) {
            System.out.println(x[0]);
        }
        return memo[m - 1][n - 1];
    }
}
```

```java
// 해설 코드 - 완전탐색
class Solution {
    public int solution(int m, int n) {
        int answer = 0;
        
        for (int r = 0; r < m; r++) {
            for (int c = 0; c < n; c++) {
                answer = dp(r, c);       
            }
        }
        
        return answer;
    }
    
    int dp(int r, int c) {
        if (r == 0 && c == 0) return 1;
        
        int unique_paths = 0;
        
        if (r - 1 >= 0) unique_paths += dp(r - 1, c);
        if (c - 1 >= 0) unique_paths += dp(r, c - 1);
        
        return unique_paths;
    }
}
```

```java
// 해설 코드 - 완전탐색 -> DP
import java.util.*;
class Solution {
    public int solution(int m, int n) {
        int answer = 0;
        int[][] memo = new int[m][n];
        for (int i = 0; i < m; i++) Arrays.fill(memo[i], -1);
        
        dp(m - 1, n - 1, memo);
        
        return memo[m - 1][n - 1];
    }
    
    int dp(int r, int c, int[][] memo) {
        if (r == 0 && c == 0) {
            memo[r][c] = 1;
            return memo[r][c];
        }
        
        if (memo[r][c] == -1) {
            int unique_paths = 0;
        
            if (r - 1 >= 0) unique_paths += dp(r - 1, c, memo);
            if (c - 1 >= 0) unique_paths += dp(r, c - 1, memo);
            
            memo[r][c] = unique_paths;
        }
        
        return memo[r][c];
    }
}
```

#### 배우게 된 점