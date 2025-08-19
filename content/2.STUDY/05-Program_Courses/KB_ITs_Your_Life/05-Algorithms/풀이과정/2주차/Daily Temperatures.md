---
tags:
  - leetcode
link: https://leetcode.com/problems/daily-temperatures/description/
weeks: 2
type: 예제
category:
  - 스택
status: Solved
solution_type:
  - 정답(답안 참고)
---
#### 문제파악
#### 접근 방법
반복문 2개로도 시간복잡도를 고려하면 $O(N^2)$
주어진 배열의 최대길이가 $10^5$ → $O(N^2)$에 넣으면 효율성테스트에서 실패 확정

스택을 이용하면 배열 한 번 읽는걸로 해결 가능하다!!! → 혁신

주어진 배열을 읽으면서 스택에 몇번째날인지 넣는다(인덱스를 스택에 넣음)
스택에 들어있는 값들의 온도가 다음에 스택에 넣을 값의 온도보다 낮으면 스택에서 제거!
며칠 기다렸는지 계산한 값을 정답 배열에 넣어주면 된다
#### 코드 구현
```java
class Solution {
    public int[] dailyTemperatures(int[] temperatures) {
        int[] answer = new int[temperatures.length];
        Deque<Integer> stack = new ArrayDeque();

        for (int today = 0; today < temperatures.length; today++) {
            while(!stack.isEmpty() && temperatures[stack.peek()] < temperatures[today]) {
                int yesterday = stack.pop();
                answer[yesterday] = today - yesterday;
            }
            stack.push(today);
        }
        return answer;
    }
}
```

#### 배우게 된 점
> [!info] 반복문이 중첩되어있다고 시간복잡도가 항상 O(N^2)인것은 아니다!!

위 코드에서 while문은 스택에 쌓인 데이터 갯수만큼만 실행됨
→ for문 전체 반복하는 동안 N번만 실행(매번 N번 실행되는게 X)

위 코드의 시간복잡도는 $O(N^2)$가 아닌 $O(2N)$ = $O(N)$
