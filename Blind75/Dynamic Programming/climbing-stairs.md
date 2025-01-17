# [Climbing Stairs](https://leetcode.com/problems/climbing-stairs/)
**Difficulty:** Easy

### Solution 1 in Java(Space Optimization)
```java
class Solution {
    public int climbStairs(int n) {
        int prev1 = 1;
        int prev2 = 1;
        for(int i=2; i<n+1; i++){
            int curr = prev2 + prev1;
            prev2 = prev1;
            prev1 = curr;
        }
        return prev1;
    }
}
```
### Solution 2 in Java(Tabulation)
```java
class Solution {
    public int climbStairs(int n) {
        int[] dp = new int[n+1];//dp[i]->total ways to reach ith stair step
        dp[0] = 1;
        dp[1] = 1;
        for(int i=2; i<n+1; i++){
            dp[i] = dp[i-1] + dp[i-2];
        }
        return dp[n];
    }
}
```
### Solution 3 in Java(Memoization)
```java
class Solution {
    public int climbStairs(int n) {
        int[] dp = new int[n+1];
        Arrays.fill(dp, -1);
        return solve(n, dp);
    }
    public int solve(int n, int[] dp){
        if(n == 0 || n == 1){
            return 1;
        }
        if(dp[n] != -1){
            return dp[n];
        }
        return dp[n] = solve(n-1, dp) + solve(n-2, dp);
    }
}
```