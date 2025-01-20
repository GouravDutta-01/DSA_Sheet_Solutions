# [Number of Ways to Reach a Position After Exactly k Steps](https://leetcode.com/problems/number-of-ways-to-reach-a-position-after-exactly-k-steps/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int numberOfWays(int startPos, int endPos, int k) {
        int mod = (int)1e9+7;
        int[][] dp = new int[3001][k+1];
        for(int[] row : dp){
            Arrays.fill(row, -1);
        }
        return solve(startPos, endPos, k, dp, mod);
    }
    public int solve(int ind, int endPos, int k, int[][] dp, int mod){
        if(k == 0){
            if(ind == endPos){
                return 1;
            }
            return 0;
        }
        if(dp[ind+1000][k] != -1){
            return dp[ind+1000][k];
        }
        int right = solve(ind+1, endPos, k-1, dp, mod);
        int left = solve(ind-1, endPos, k-1, dp, mod);
        return dp[ind+1000][k] = (left+right)%mod;
    }
}
```