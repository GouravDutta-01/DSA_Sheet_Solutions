# [Find the Winner of the Circular Game](https://leetcode.com/problems/find-the-winner-of-the-circular-game/description/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int findTheWinner(int n, int k) {
        return solve(n, k) + 1;
    }
    public int solve(int n, int k){
        if(n == 1){
            return 0;
        }
        return (solve(n-1, k) + k) % n;
    }
} 
```
