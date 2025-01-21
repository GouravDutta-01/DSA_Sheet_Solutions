# [Count Collisions on a Road](https://leetcode.com/problems/count-collisions-on-a-road/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int countCollisions(String directions) {
        int count = 0;
        Stack<Character> stack = new Stack<>();
        for(char ch : directions.toCharArray()){
            char car = ch;
            if(!stack.isEmpty() && stack.peek() == 'R' && car == 'L'){
                stack.pop();
                count += 2;
                car = 'S';
            }
            if(!stack.isEmpty() && stack.peek() == 'S' && car == 'L'){
                stack.pop();
                count++;
                car = 'S';
            }
            while(!stack.isEmpty() && stack.peek() == 'R' && car == 'S'){
                stack.pop();
                count++;
                car = 'S';
            }
            stack.push(car);
            
        }
        return count;    
    }
}
```