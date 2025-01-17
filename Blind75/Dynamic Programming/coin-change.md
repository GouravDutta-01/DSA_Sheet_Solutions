# [Coin Change](https://leetcode.com/problems/coin-change/)
**Difficulty:** Medium

### Solution 1 in Java(Space Optimization)
```java

```
### Solution 2 in Java(Tabulation)
```java

```
### Solution 3 in Java(Memoization)
```java
class Solution {
    public int coinChange(int[] coins, int amount) {
        int[][] dp = new int[coins.length][amount+1];
        for(int[] row : dp){
            Arrays.fill(row, -1);
        }
        int ans = solve(coins.length-1, coins, amount, dp);
        return ans == (int)1e9 ? -1 : ans;    
    }
    public int solve(int ind, int[] coins, int amount, int[][] dp){
        if(amount == 0){
            return 0;
        }
        if(ind == 0){
            return (amount%coins[0] == 0) ? amount/coins[0] : (int)1e9;
        }
        if(dp[ind][amount] != -1){
            return dp[ind][amount];
        }
        int take = (int)1e9;
        if(coins[ind] <= amount){
            take = 1 + solve(ind, coins, amount-coins[ind], dp);
        }
        int notTake = solve(ind-1, coins, amount, dp);
        return dp[ind][amount] = Math.min(take, notTake);
    }
}
```