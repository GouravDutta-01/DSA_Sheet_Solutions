# [House Robber](https://leetcode.com/problems/house-robber/)
**Difficulty:** Medium

### Solution 1 in Java(Space Optimization)
```java

```
### Solution 2 in Java(Tabulation)
```java
class Solution {
    public int rob(int[] nums) {
        int n = nums.length;
        int[] dp = new int[n];
        dp[0] = nums[0];
        for(int i=1; i<n; i++){
            int take = nums[i];
            int notTake = 0;
            if(i-2 >= 0){
                take += dp[i-2];
            }
            if(i-1 >= 0){
                notTake = dp[i-1];
            }
            dp[i] = Math.max(take, notTake);
        }
        return dp[n-1];
    }
}
```
### Solution 3 in Java(Memoization)
```java
class Solution {
    public int rob(int[] nums) {
        int[] dp = new int[nums.length];
        Arrays.fill(dp, -1);
        return solve(0, nums, dp);
    }
    public int solve(int ind, int[] nums, int[] dp){
        if(ind >= nums.length){
            return 0;
        }
        if(dp[ind] != -1){
            return dp[ind];
        }
        int take = nums[ind] + solve(ind+2, nums, dp);
        int notTake = solve(ind+1, nums, dp);
        return dp[ind] = Math.max(take, notTake);
    }
}
```