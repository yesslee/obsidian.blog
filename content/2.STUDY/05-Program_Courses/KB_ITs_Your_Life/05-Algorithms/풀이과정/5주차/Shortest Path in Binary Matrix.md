---
tags:
  - leetcode
link: https://leetcode.com/problems/shortest-path-in-binary-matrix/description/
weeks: 5
type: 예제
category:
  - 그래프
  - BFS
status: Solved
solution_type:
  - 정답(답안 참고)
---
#### 문제파악
n * n 바이너리 행렬 grid가 주어짐

주어진 grid에서 가장 짧은 경로의 길이를 return하기

갈 수 있는 경로가 없으면 -1 return

시작점: (0, 0), 목적지: (n, n)

경로는 0으로 표시, 상하좌우대각선 8방향으로 이동 가능
#### 접근 방법
**가장 짧은 경로**의 길이 → DFS는 최단거리 보장 X = BFS를 사용하자!!
#### 코드 구현
```java
class Solution {
    static int rowLength, colLength;
    static boolean[][] visited;
    int[] dr = {0, 1, 1, 1, 0, -1, -1, -1};
    int[] dc = {1, 1, 0, -1, -1, -1, 0, 1};

    public boolean isValid(int r, int c, int[][] grid) {
        return (r >= 0 && r < rowLength) && (c >= 0 && c < colLength) && (grid[r][c] == 0);
    }

    public int shortestPathBinaryMatrix(int[][] grid) {
        int shortestDist = -1;
        rowLength = grid.length;
        colLength = grid[0].length;
        
        if (grid[0][0] != 0 || grid[rowLength - 1][colLength - 1] != 0) {
	    	return shortestDist;
	    }

        visited = new boolean[rowLength][colLength];
        
        Queue<int[]> queue = new ArrayDeque<>();
        queue.offer(new int[]{0, 0, 1});
        visited[0][0] = true;

        while (!queue.isEmpty()) {
            int[] curPos = queue.poll();
            int curRow = curPos[0];
            int curCol = curPos[1];
            int curDist = curPos[2];

            if (curRow == rowLength - 1 && curCol == colLength - 1) {
                shortestDist = curDist;
                break;
            }

            for (int i = 0; i < 8; i++) {
                int nextRow = curRow + dr[i];
                int nextCol = curCol + dc[i];
                
                if (isValid(nextRow, nextCol, grid)) {
                    if (!visited[nextRow][nextCol]) {
                        queue.offer(new int[]{nextRow, nextCol, curDist + 1});
                        visited[nextRow][nextCol] = true;
                    }
                }
            }
        }
        return shortestDist;
    }
}
```

#### 배우게 된 점