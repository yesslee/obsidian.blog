---
tags:
  - leetcode
link: https://leetcode.com/problems/permutations/
weeks: 3
type: 예제
category:
  - 순열조합
  - 완전탐색
status: Solved
solution_type:
  - 정답(답안 참고)
---
#### 문제파악
~~백준의 N과 M 문제랑 로직 비슷한 문제 같기도??~~

nums 배열(중복된 숫자 없이 정수로만 이루어진 배열)로 만들 수 있는 모든 순열을 반환한다
#### 접근 방법
순열 = 중복 없이 순서 고려한(Ordered) 나열
nums 배열에 중복된 요소 존재 X

nums 배열을 순회하며 순열을 만드는 배열에 요소를 추가
nums의 각 요소 방문 여부는 visited라는 배열을 만들어서 체크
→ 요소 추가한 뒤에는 더이상 해당 요소 비교 안하도록 (필요없는 작업 반복하지 않게하여 효율성 높임) = 백트래킹?

요소를 추가하면서 nums의 길이와 만들어진 순열 배열의 길이가 같아지면 완성된 배열 조합을 넣는 리스트에 추가
⇒ 위 과정 재귀를 통해서 반복?
#### 코드 구현
```java
class Solution {
		// 완성된 순열을 넣는 리스트는 전역변수로 설정
    List<List<Integer>> result = new ArrayList<>();
    public List<List<Integer>> permute(int[] nums) {
        boolean[] visited = new boolean[nums.length];
        backtrack(new ArrayList<>(), nums, visited);

        return result;
    }
    
    // 백트래킹 진행할 재귀함수
    void backtrack(List<Integer> permu, int[] nums, boolean[] visited) {
        // basecase
        if (permu.size() == nums.length) { // 순열 만드는 배열의 길이가 nums 배열의 길이와 같아지는 시점이 하나의 순열이 완성된 시점
            result.add(new ArrayList<>(permu)); // 완성된 하나의 순열을 결과 출력할 리스트에 추가
            return; // 재귀 탈출
        }

        // recursive call
        for (int i = 0; i < nums.length; i++) {
            if (visited[i]) continue; // 방문한 요소라면 pass

            permu.add(nums[i]); // 첫 방문인 요소라면 순열 만드는 배열에 해당 요소 추가
            visited[i] = true; // 방문한 요소임을 체크
            backtrack(permu, nums, visited);
            permu.remove(permu.size() - 1); 
            visited[i] = false;
        }
    }
}
```

#### 배우게 된 점