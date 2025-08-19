---
tags:
  - leetcode
link: https://leetcode.com/problems/network-delay-time/description/
weeks: 8
type: 예제
category:
  - 다익스트라
status: Solved
solution_type:
  - 정답(스스로 풀이)
---
#### 문제파악
`times = [출발노드, 도착노드, 가중치]` 형태의 리스트들로 구성된 2차원 배열
- n = 노드 갯수
- k = 시작 노드

**n개의 노드를 전부 도착하기 위한 최소시간 return**

특정 노드에 도착 불가능하다면 -1 return
#### 접근 방법
가중치 그래프 & 최소 시간 → 다익스트라 알고리즘으로 푸는 문제!

**n개의 노드를 전부 도착하기 위한 최소시간** return
⇒ **최소시간 중 가장 큰 값**을 return해줘야 함

특정 노드에 도착 불가능하다면 -1 return

⇒ 다익스트라로 최소시간 다 구했는데 특정 노드에 INF가 하나라도 존재하면 -1 return?

다익스트라로 각 노드별 누적 최소 비용 구하고 나면 해당 값들이 distance 배열에 담기게 되므로, 그 중 최대값을 return 하면 된다!

그러나 다익스트라 끝냈는데도 방문 못한 노드(=도착 불가능한 노드)는 INF 값 그대로일 것이므로 최대값이 INF와 동일하다면 -1 return
#### 코드 구현
```java
class Edge implements Comparable<Edge> {
    int node, cost;
    public Edge(int node, int cost) {
        this.node = node;
        this.cost = cost;
    }

    @Override
    public int compareTo(Edge other) {
        return Integer.compare(this.cost, other.cost);
    }

		// 인접리스트에 값 잘 들어갔는지 확인 출력용
    // @Override
    // public String toString() {
    //     return "Edge{" +
    //             "node=" + node +
    //             ", cost=" + cost +
    //             '}';
    // }
}

// Comparator 사용하는 경우
class Edge {
    int node, cost;
    public Edge(int node, int cost) {
        this.node = node;
        this.cost = cost;
    }
}

class Solution {
    public int networkDelayTime(int[][] times, int n, int k) {
        Map<Integer, List<Edge>> graph = new HashMap<>();
        for (int i = 1; i <= n; i++) {
            graph.put(i, new ArrayList<>());
        }

        for (int[] time : times) {
            graph.get(time[0]).add(new Edge(time[1], time[2]));
        }

        return dijkstra_max(graph, k, n, graph.size());
    }

    int dijkstra_max(Map<Integer, List<Edge>> graph, int start, int end, int n) {
        int INF = Integer.MAX_VALUE;
        int[] distance = new int[n + 1];
        Arrays.fill(distance, INF);

        Queue<Edge> pq = new PriorityQueue<>();
        /*
        // Comparator를 사용하여 PriorityQueue를 정의(compareTo 메소드 정의 안하고 사용 가능한 방법)
        Queue<Edge> pq = new PriorityQueue<>(Comparator.comparingInt(edge -> edge.cost));
        */
        pq.add(new Edge(start, 0));
        distance[start] = 0;

        while (!pq.isEmpty()) {
            Edge current = pq.remove();
            if (distance[current.node] < current.cost) {
                continue;
            }

            for (Edge next : graph.get(current.node)) {
                int nextCost = distance[current.node] + next.cost;
                if (nextCost < distance[next.node]) {
                    pq.add(new Edge(next.node, nextCost));
                    distance[next.node] = nextCost;
                }
            }
        }

        int max_cost = -1;
        // distance 배열은 노드 1부터 시작하는 값에 맞췄기 때문에 0부터가 아닌 1부터 확인해야함에 주의
        for (int i = 1; i <= n; i++) {
            max_cost = Math.max(max_cost, distance[i]);
        }

        if (max_cost == INF) return -1;

        return max_cost;
    }
}
```

```java
// 해설집 코드
class Solution {
    public int networkDelayTime(int[][] times, int n, int k) {
        //✅ 인풋을 본인이 쓰기 편한 구조로 바꾸기 => 방향 그래프 만들기
        Map<Integer, List<int[]>> edges = Arrays.stream(times)
            .collect(Collectors.groupingBy(t -> t[0]));
        int[] visited = new int[n+1];
        Arrays.fill(visited, Integer.MAX_VALUE);
        // 큐에는 { 정점, 거리 } 형태의 배열이 들어간다.
        Queue<int[]> pq = new PriorityQueue<>((e1, e2) -> e1[1] - e2[1]);
        pq.add(new int[]{ k, 0 });
        visited[k] = 0;

				//✅ k로부터 모든 노드들의 최단거리 구하기 => 다익스트라 알고리즘 수행
        int maxTime = 0;
        int visitCount = 1;
        while (!pq.isEmpty()) {
            int[] cur = pq.remove();
            int u = cur[0], time = cur[1];
            if (visited[u] < time) continue;
            maxTime = time;

            // 연결된 모든 간선에 대해 탐색한다.
            if (!edges.containsKey(u)) continue;
            for (int[] edge : edges.get(u)) {
                int v = edge[1], w = edge[2];
                // 이미 더 짧은 거리로 방문한 적이 있는 경우 건너뛴다.
                if (time + w >= visited[v]) continue;

                // 처음 방문했다면 visitCount++
                if (visited[v] == Integer.MAX_VALUE) visitCount++;
								//✅ 다익스트라가 수행되며 각 노드까지의 최단 거리 저장 
                visited[v] = time + w;
                pq.add(new int[]{ v, time + w });
            }
        }
				//✅ k노드로 부터 도달할 수 없는 노드가 존재하는 경우 -1을 반환한다.
				//✅ 그 외의 경우 저장된 최단 거리 중 최대값을 반환한다.
        return visitCount == n ? maxTime : -1;
    }
}
```

#### 배우게 된 점
compareTo 말고도 다른 정렬방법 존재 → Comparator!
```java
// Comparator를 사용하여 PriorityQueue를 정의(compareTo 메소드 정의 안하고 사용 가능한 방법)
Queue<Edge> pq = new PriorityQueue<>(Comparator.comparingInt(edge -> edge.cost));
```

두 매개변수의 차이 결과값에 따라 오름차순/내림차순 정렬된다(단, 반환값은 int인 경우만 정렬 가능)