---
tags:
  - leetcode
link: https://leetcode.com/problems/two-sum/description/
weeks: 1
type: 예제
category:
  - 완전탐색
  - 정렬
  - 투포인터
  - 문자열
  - 해시테이블
status: Solved
solution_type:
  - 정답(스스로 풀이)
---
#### 문제파악
#### 접근 방법
#### 코드 구현
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] idx = new int[2];
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[j] == target) {
                    idx[0] = i;
                    idx[1] = j;
                }
            }
        }
        return idx;
    }
}
```

#### 배우게 된 점
- 정렬과 two pointer를 이용한 해결 방법
- 해시맵을 이용한 해결 방법
