---
tags:
  - leetcode
link: https://leetcode.com/problems/keys-and-rooms/description/
weeks: 4
type: 예제
category:
  - 그래프
status: In Progress
solution_type:
---
#### 문제파악
#### 접근 방법
노드 간 연결성 판단할때도 BFS, DFS 사용
→ 연결된 모든 노드를 방문한다는 특성 사용하는 것이기 때문에 어느 것으로 구현하든 상관 X

bfs, dfs 이용해서 lockers의 노드들 방문 여부 체크하여 방문하지 않은 노드가 있다면 false 리턴, 모두 방문한 경우 true 리턴
#### 코드 구현
```java
// bfs
class Solution {
    static boolean[] visited;
    public boolean canVisitAllRooms(List<List<Integer>> rooms) {
        visited = new boolean[rooms.size()];
        bfs(rooms, 0);

        for (int i = 0; i < visited.length; i++) {
            if (!visited[i]) {
                return false;
            }
        }
        return true;
    }

    public void dfs(List<List<Integer>> rooms, int v) {
        visited[v] = true;

        for (Integer nextVertex : rooms.get(v)) {
            if (!visited[nextVertex]) {
                dfs(rooms, nextVertex);
            }
        }
    }

    public void bfs(List<List<Integer>> rooms, int v) {
        Queue<Integer> queue = new ArrayDeque<>();        
        visited[v] = true;
        queue.offer(v);

        while(!queue.isEmpty()) {
            int currVertex = queue.poll();
            for (Integer nextVertex : rooms.get(currVertex)) {
                if (!visited[nextVertex]) {
                    queue.offer(nextVertex);
                    visited[nextVertex] = true;
                }
            }
        }
    }
}
```

```java
// dfs
class Solution {
    static boolean[] visited;
    public boolean canVisitAllRooms(List<List<Integer>> rooms) {
        visited = new boolean[rooms.size()];

        dfs(rooms, 0);

        for (int i = 0; i < visited.length; i++) {
            if (!visited[i]) {
                return false;
            }
        }
        return true;
    }

    public void dfs(List<List<Integer>> rooms, int v) {
        visited[v] = true;

        for (Integer nextVertex : rooms.get(v)) {
            if (!visited[nextVertex]) {
                dfs(rooms, nextVertex);
            }
        }
    }
}
```

#### 배우게 된 점