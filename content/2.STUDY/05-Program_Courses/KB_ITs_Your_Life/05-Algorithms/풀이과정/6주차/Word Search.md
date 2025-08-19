---
tags:
  - leetcode
link: https://leetcode.com/problems/word-search/description/
weeks: 6
type: 예제
category:
  - 백트래킹
  - 완전탐색
status: In Progress
solution_type:
---
#### 문제파악
그래프 문제는 아니지만 그래프 문제로 해석 가능(그리드 주어짐)

완전탐색 챌린지 문제였음

---

주어진 그리드(board)에서 상하좌우로만 연결해서 주어진 단어를 만들 수 있으면 true, 만들 수 없으면 false 리턴
#### 접근 방법
주어진 단어에서 시작하는 글자를 먼저 찾는다
그리드에 시작하는 글자의 위치를 찾은 뒤, 해당 위치에서 BFS/DFS 실행?
→ 시작하는 단어 없으면 바로 false 리턴?

모든 방향에 대해서 주어진 word와 일치하면 true 반환
word와 일치 = 상하좌우에 대해 word와 일치하는지 판별
#### 코드 구현
```java
// 구현 시도 코드
class Solution {
    boolean[][] visited;
    int[] dr = {1, 0, -1, 0};
    int[] dc = {0, 1, 0, -1};
    public boolean exist(char[][] board, String word) {
        char startAlp = word.charAt(0);
        int start_r = -1;
        int start_c = -1;
        int word_idx = 1;
        String target = "" + startAlp;

        for (int r = 0; r < board.length; r++) {
            for (int c = 0; c < board[r].length; c++) {
                if (board[r][c] == startAlp) {
                    start_r = r;
                    start_c = c;
                }
            }
        }

        if (start_r == -1 || start_c == -1) return false;

        // bfs
        Queue<int[]> queue = new LinkedList<>();
        visited = new boolean[board.length][board[0].length];
        queue.offer(new int[]{start_r, start_c});
        visited[start_r][start_c] = true;

        while (!queue.isEmpty()) {
            int[] curr = queue.poll();
            int curr_r = curr[0];
            int curr_c = curr[1];

            for (int i = 0;  i < 4; i++) {
                if (word_idx >= word.length()) return true;
                int next_r = curr_r + dr[i];
                int next_c = curr_c + dc[i];

                if ((0 <= next_r && next_r < board.length) && (0 <= next_c && next_c < board[0].length)) {
                    if (word.charAt(word_idx) == board[next_r][next_c]){
                        if (!visited[next_r][next_c]) {
                            target += board[next_r][next_c];
                            System.out.println(target);
                            queue.offer(new int[]{next_r, next_c});
                            visited[next_r][next_c] = true;
                            return false;
                        }
                    }
                }
            }
            
        }

        return true;
    }
}
```

```java
// 수업 중 해설 코드
import java.util.*;
class Solution {
    int m;
    int n;
    int[] dr = {1, -1, 0, 0};
    int[] dc = {0, 0, 1, -1};
    boolean[][] visited;
    public boolean exist(char[][] board, String word) {
        m = board.length;
        n = board[0].length;
        visited = new boolean[m][n];
        for (int r = 0; r < m; r++){
            for (int c = 0; c < n; c++){
                if (board[r][c] == word.charAt(0)){
                    visited[r][c] = true;
                    if (backtrack(r,c, 1, board, word)) return true;
                    visited[r][c] = false;
                }
                
            }
        }
        return false;

    }
    
    // 주어진 word랑 일치하면 True 반환
    boolean backtrack(int r, int c, int count, char[][] board, String word) {
        // 디버깅용 출력
        System.out.println(r + "" + c + "" + board[r][c]);
        if (count >= word.length()) return true;
        // 상하좌우가 주어진 word랑 일치하는지 판별
        for (int i = 0 ; i < 4; i ++){
            int nr = r + dr[i];
            int nc = c + dc[i];

            if (nr >= 0 && nr < m && nc >=0 && nc < n){
                if (board[nr][nc] == word.charAt(count)){
                    if (visited[nr][nc]) continue;
                    visited[nr][nc] = true;
                    if (backtrack(nr,nc, count+1, board, word)) return true;
                    visited[nr][nc] = false;
                }
            }
        }
        return false;

    }
}
```

#### 배우게 된 점