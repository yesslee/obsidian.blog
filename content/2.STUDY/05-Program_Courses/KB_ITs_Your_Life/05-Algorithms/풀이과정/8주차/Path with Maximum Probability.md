---
tags:
  - leetcode
link: https://leetcode.com/problems/path-with-maximum-probability/description/
weeks: 8
type: 실습
category:
  - 다익스트라
status: Solved
solution_type:
  - 정답(답안 참고)
  - 오답(스스로 풀이)
---
#### 문제파악
- n = 노드 갯수
- edges = 2차원 배열로 표현한 무방향 그래프
- succProb = edges의 각 노드 간 가중치(= 성공확률)가 적힌 배열
- start_node = 출발점 노드
- end_node = 도착점 노드

출발점 노드에서 도착점 노드까지 가장 높은 확률로 도달할 수 있는 확률을 return

도달 불가능하면 0 return

(return type은 double인 점 주의)
#### 접근 방법
다익스트라 → 누적(더하기)된 cost에서 최솟값 찾아야 했다

maximum probability = 최대 **확률** 구해야 함
⇒ 확률은 덧셈 아닌 **곱셈**!
#### 코드 구현
```java
// 구현 시도 코드
import java.util.*;
class Edge implements Comparable<Edge> {
    int node;
    double prob;
    public Edge(int node, double prob) {
        this.node = node;
        this.prob = prob;
    }

    @Override
    public int compareTo(Edge other) {
        return Double.compare(this.prob, other.prob);
        // 이 부분이 핵심적!(문제 해결 실패한 핵심 원인)
    }

    @Override
    public String toString() {
        return "node=" + node + ", prob=" + prob;
    }
}

class Solution {
    public double maxProbability(int n, int[][] edges, double[] succProb, int start_node, int end_node) {
        Map<Integer, List<Edge>> graph = new HashMap<>();
        for (int i = 0; i < n; i++) graph.put(i, new ArrayList<>());
        for (int i = 0; i < edges.length; i++) {
            graph.get(edges[i][0]).add(new Edge(edges[i][1], succProb[i]));
            graph.get(edges[i][1]).add(new Edge(edges[i][0], succProb[i]));
        }

        // System.out.println(graph);

        return dijkstra(graph, start_node, end_node, succProb, graph.size());
    }
    
    double dijkstra(Map<Integer, List<Edge>> graph, int start, int end, double[] succProb, int n) {
        double[] probs = new double[n];
        Arrays.fill(probs, -1); // 확률이기 때문에 0으로 넣으면 됐었다

        Queue<Edge> pq = new PriorityQueue<>();
        
        // 방문할 확률이므로 시작점 노드는 100% 확률로 방문 = 1로 초기화했어야 함!
        pq.add(new Edge(start, succProb[start]));
        probs[start] = succProb[start];

        while (!pq.isEmpty()) {
            Edge current = pq.remove();
            if (probs[current.node] < current.cost) {
                continue;
            }

            for (Edge next : graph.get(current.node)) {
                double nextCost = probs[current.node] * next.cost; // 확률은 곱으로 구해야 함
                if (probs[next.node] < nextCost) {
                    pq.add(new Edge(next.node, nextCost));
                    probs[next.node] = nextCost;
                }
            }
        }

        // double max_prob = -1.0;
        // for (int i = 0; i < probs.length; i++) {
        //     max_prob = Math.max(max_prob, probs[i]);
        // }
        // System.out.println("max_prob: " + max_prob);

        for (double i : probs) {
            System.out.println(i);
        }

        return probs[end];
    }
}
```

```java
// 정답 코드
import java.util.*;
class Edge implements Comparable<Edge> {
    int node;
    double prob;
    public Edge(int node, double prob) {
        this.node = node;
        this.prob = prob;
    }

    @Override
    public int compareTo(Edge other) {
        return Double.compare(other.prob, this.prob);
        // 큰 값 기준이기 때문에 매개변수 순서가 기존 다익스트라 코드와 달라짐에 주의
    }

    @Override
    public String toString() {
        return "node=" + node + ", prob=" + prob;
    }
}

class Solution {
    public double maxProbability(int n, int[][] edges, double[] succProb, int start_node, int end_node) {
        // 인접 리스트 변환
        Map<Integer, List<Edge>> graph = new HashMap<>();
        for (int i = 0; i < n; i++) graph.put(i, new ArrayList<>());
        for (int i = 0; i < edges.length; i++) {
            graph.get(edges[i][0]).add(new Edge(edges[i][1], succProb[i]));
            graph.get(edges[i][1]).add(new Edge(edges[i][0], succProb[i]));
        }

        return dijkstra(graph, start_node, end_node, succProb, graph.size());
    }
    
    double dijkstra(Map<Integer, List<Edge>> graph, int start, int end, double[] succProb, int n) {
        // 기존 다익스트라 - 누적 값 중 최솟값 min(cost + cost)
        // 해당 문제 적용 - 누적 확률 곱 중 최대값 max(prob * prob)

        //초기 설정
        double[] probs = new double[n];
        Arrays.fill(probs, 0.0); // 최대 확률이므로 최소값 0으로 초기화;

        // 다익스트라 진행
        Queue<Edge> pq = new PriorityQueue<>();
        
        /*
        // Comparator를 사용하여 PriorityQueue를 정의
        Queue<Edge> pq = new PriorityQueue<>(Comparator.comparingDouble(probs.prob -> probs));
        */
        
        // 시작점 초기화
        // 방문할 확률이므로 시작점 노드는 100% 확률로 방문 = 1로 초기화!
        pq.add(new Edge(start, 1.0));
        probs[start] = 1.0;

        while (!pq.isEmpty()) {
            // 방문
            Edge current = pq.remove();
            if (probs[current.node] < current.prob) {
                continue;
            }

            // 예약
            for (Edge next : graph.get(current.node)) {
                double nextProb = probs[current.node] * next.prob; // 확률은 곱으로 구해야 함
                if (probs[next.node] < nextProb) {
                    pq.add(new Edge(next.node, nextProb));
                    probs[next.node] = nextProb;
                }
            }
        }

        // for (double i : probs) {
        //     System.out.println(i);
        // }

        return probs[end];
    }
}
```
#### 배우게 된 점
~~사실 다익스트라 함수로 따로 안 빼고 내부에서 구현해도 된다…~~

compare() 비교 매개변수 넣는 순서 정말정말 중요하다!!!

Comparator 사용하고 싶은 경우, 정렬할 값이 Double이기 때문에 Network Delay Time에서 사용한 `Comparator.comparingInt()`는 사용 불가!

```java
// Comparator를 사용하여 PriorityQueue를 정의(compareTo 메소드 정의 안하고 사용 가능한 방법)
Queue<Edge> pq = new PriorityQueue<>(Comparator.comparingInt(edge -> edge.cost));
```

`Double.compare()`를 익명 클래스를 이용하여 Override해서 사용하거나, 람다 표현식을 이용해야 함!

```java
// Comparator - 익명 클래스 사용하여 구현
Queue<Edge> pq = new PriorityQueue<>(new Comparator<Edge>() {
    @Override
    public int compare(Edge e1, Edge e2) {
        return Double.compare(e2.prob, e1.prob); // 높은 확률이 우선
    }
});

// Comparator - 람다 표현식 사용하여 구현
Queue<Edge> pq = new PriorityQueue<>((e1, e2) -> Double.compare(e2.prob, e1.prob));
```