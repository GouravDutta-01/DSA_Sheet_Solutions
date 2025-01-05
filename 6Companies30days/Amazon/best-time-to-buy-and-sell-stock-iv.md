# [Best Time to Buy and Sell Stock IV](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-iv/)
**Difficulty:** Hard

### Solution 1 in Java (Memoization) 
```java
class Solution {
    public int maxProfit(int k, int[] prices) {
        int[][][] dp = new int[prices.length][2][k+1];
        for(int[][] temp1 : dp){
            for(int[] temp2 : temp1){
                Arrays.fill(temp2, -1);
            }
        }
        return solve(0, 1, k, prices, dp);
    }
    public int solve(int ind, int canBuy, int k, int[] prices, int[][][] dp){
        if(k == 0){
            return 0;
        }
        if(ind == prices.length){
            return 0;
        }
        if(dp[ind][canBuy][k] != -1){
            return dp[ind][canBuy][k];
        }
        int take = 0;
        int notTake = 0;
        if(canBuy == 1){
            take = -prices[ind] + solve(ind+1, 0, k, prices, dp);
            notTake = solve(ind+1, 1, k, prices, dp);
        }
        else{
            take = prices[ind] + solve(ind+1, 1, k-1, prices, dp);
            notTake = solve(ind+1, 0, k, prices, dp);
        }
        return dp[ind][canBuy][k] = Math.max(take, notTake);
    }
}
```
