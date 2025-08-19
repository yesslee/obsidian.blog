---
tags:
  - leetcode
link: https://leetcode.com/problems/number-of-islands/
weeks: 5
type: 예제
category:
  - 그래프
  - BFS
  - DFS
status: Solved
solution_type:
  - 정답(스스로 풀이)
---
#### 문제파악
m * n 형태의 grid가 주어지며 1 = 땅, 0 = 물을 의미함

섬(island)은 상하좌우 4방향으로 땅 연결되어있는 범위를 섬 하나로 취급함

주어진 그리드 가장자리 범위는 벗어나면 안됨
#### 접근 방법
연결된 모든 노드 탐색하는 문제 = BFS/DFS 어느걸로 구현하든 상관 없음!

bfs/dfs 실행 → visited 표시 진행

방문 안 한 1 → bfs/dfs 실행 할 때마다 카운트 +1

~ pseudo code ~
```
이중 for문으로 grid 하나씩 돌면서
	방문 안한 노드 && grid 값이 1일때만
		bfs/dfs 실행하고
		카운트 + 1하기
```

bfs/dfs는 라이브러리에서 함수 가져다 쓰듯이 외워두고 바로 구현 가능한 수준이 되어야 함!!
#### 코드 구현
```java
// DFS 구현
class Solution {
    static int rowLength, colLength;
    static boolean[][] visited;
    int[] dr = {1, 0, -1, 0};
    int[] dc = {0, 1, 0, -1};
    
    public boolean isValid(int r, int c, char[][] grid) {
        return (r >= 0 && r < rowLength) && (c >= 0 && c < colLength) && (grid[r][c] == '1');
    }

    public void dfs(int r, int c, char[][] grid) {
        visited[r][c] = true;

        for (int i = 0; i < 4; i++) {
            int nextRow = r + dr[i];
            int nextCol = c + dc[i];
            if (isValid(nextRow, nextCol, grid)) {
                if (!visited[nextRow][nextCol]) {
                    dfs(nextRow, nextCol, grid);
                }
            }
        }
    }
    
    public int numIslands(char[][] grid) {
        int count = 0;
        rowLength = grid.length;
        colLength = grid[0].length;

        visited = new boolean[rowLength][colLength];

        for (int i = 0; i < rowLength; i++) {
            for (int j = 0; j < colLength; j++) {
                if ((grid[i][j] == '1') && (!visited[i][j])) {
                    dfs(i, j, grid);
                    count++;
                }
            }
        }
        return count;
    }
}
```

```java
// BFS 구현
class Solution {
    static int rowLength, colLength;
    static boolean[][] visited;
    int[] dr = {1, 0, -1, 0};
    int[] dc = {0, 1, 0, -1};
    
    public boolean isValid(int r, int c, char[][] grid) {
        return (r >= 0 && r < rowLength) && (c >= 0 && c < colLength) && (grid[r][c] == '1');
    }

    public void bfs(int r, int c, char[][] grid) {
        Queue<int[]> queue = new ArrayDeque<>();
        queue.offer(new int[]{r, c});
        visited[0][0] = true;
        
        while (!queue.isEmpty()) {
            int[] curPos = queue.poll();
            int curRow = curPos[0];
            int curCol = curPos[1];

            for (int i = 0; i < 4; i++) {
                int nextRow = curRow + dr[i];
                int nextCol = curCol + dc[i];
                if (isValid(nextRow, nextCol, grid)) {
                    if (!visited[nextRow][nextCol]) {
                        queue.offer(new int[]{nextRow, nextCol});
                        visited[nextRow][nextCol] = true;
                    }
                }
            }
        }
    }

    public int numIslands(char[][] grid) {
        int count = 0;
        rowLength = grid.length;
        colLength = grid[0].length;

        visited = new boolean[rowLength][colLength];

        for (int i = 0; i < rowLength; i++) {
            for (int j = 0; j < colLength; j++) {
                if ((grid[i][j] == '1') && (!visited[i][j])) {
                    bfs(i, j, grid);
                    count++;
                }
            }
        }
        return count;
    }
}
```

#### 배우게 된 점
함수 구현은 잘 했는데 isValid에서 1 체크하는 부분을 char가 아닌 int로 넣었어서 오답으로 나왔었다…ㅠ 타입 확인을 잘 하자
