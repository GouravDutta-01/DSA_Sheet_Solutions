# [Number of People Aware of a Secret](https://leetcode.com/problems/number-of-people-aware-of-a-secret/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int peopleAwareOfSecret(int n, int delay, int forget) {
        int mod = (int)1e9+7;
        int[] dp = new int[n+1];
        Arrays.fill(dp, -1);
        return (solve(n, delay, forget, mod, dp)-solve(n-forget, delay, forget, mod, dp)+mod)%mod;
    }
    public int solve(int n, int delay, int forget, int mod, int[] dp){
        if(n <= 0){
            return 0;
        }
        if(dp[n] != -1){
            return dp[n];
        }
        int total = 1;
        for(int i=delay; i<forget; i++){
            total = (total+solve(n-i, delay, forget, mod, dp))%mod;
        }
        return dp[n] = total;
    }
}
```
