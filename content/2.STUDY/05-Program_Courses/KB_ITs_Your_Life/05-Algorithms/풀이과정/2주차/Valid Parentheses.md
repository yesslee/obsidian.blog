---
tags:
  - leetcode
link: https://leetcode.com/problems/valid-parentheses/
weeks: 2
type: 예제
category:
  - 스택
status: Solved
solution_type:
  - 정답(스스로 풀이)
---
#### 문제파악
여는 괄호와 닫는 괄호들로 이루어진 String이 주어지고, 해당 괄호들이 여는 괄호와 닫는 괄호가 알맞게 짝지어지면 유효한 괄호이므로 true를 반환하고, 아니라면 false를 반환한다.

**유효한 괄호 예시**
`()`
`(){}[]`

**유효하지 않은 괄호 예시**
`(]` ← 열고닫는 괄호가 맞긴 하지만 소괄호 - 대괄호 짝이므로 안맞음
`([)`
#### 접근 방법
유효한 괄호 짝맞추기 = 스택 사용하자!

문자열 하나씩 읽으면서 여는 괄호라면 스택에 넣고 다음 문자열을 읽는다.

스택이 비어있지 않고, 다음 문자열이 닫는 괄호라면 스택에 가장 마지막으로 들어간 요소가 닫는 괄호의 짝과 맞는지 비교해서 맞다면 스택에서 제거한다.

위 과정을 반복한 뒤, 스택에 남아있는 괄호가 있는지 확인하여 남아있다면 유효하지 않은 괄호이므로 false를 반환하고, 스택이 비어있다면 유효한 괄호이므로 true를 반환한다.
#### 코드 구현
```java
class Solution {
    public boolean isValid(String s) {
        Deque<Character> stack = new ArrayDeque();

        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == '(' || s.charAt(i) == '{' || s.charAt(i) == '[') {
                stack.push(s.charAt(i));
            } else if (!stack.isEmpty()) {
                if (s.charAt(i) == ')' && stack.peek() == '(') stack.pop();
                else if (s.charAt(i) == '}' && stack.peek() == '{') stack.pop();
                else if (s.charAt(i) == ']' && stack.peek() == '[') stack.pop();
                else stack.push(s.charAt(i));
            } else {
                stack.push(s.charAt(i));
            }
        }
        if (stack.isEmpty()) return true;
            
        return false; 
    }
}
```

#### 배우게 된 점
- Stack 클래스의 성능 이슈 때문에 스택 구현 시에는 Deque와 ArrayDeque로 구현하는게 좋다는 점을 배우게 되었다!
