# [Number following a pattern](https://www.geeksforgeeks.org/problems/number-following-a-pattern3126/1)
**Difficulty:** Medium

### Solution in Java
```java
class Solution{
    static String printMinNumberForPattern(String S){
        StringBuilder sb = new StringBuilder();
        int val = 1;
        Stack<Integer> stack = new Stack<>();
        for(int i=0; i<S.length(); i++){
            stack.push(val);
            val++;
            if(S.charAt(i) == 'I'){
                while(!stack.isEmpty()){
                    sb.append(stack.pop());
                }
            }
        }
        stack.push(val);
        while(!stack.isEmpty()){
            sb.append(stack.pop());
        }
        return sb.toString();
    }
}
```