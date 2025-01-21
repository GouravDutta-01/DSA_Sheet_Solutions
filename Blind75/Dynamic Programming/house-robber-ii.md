# [House Robber II](https://leetcode.com/problems/house-robber-ii/)
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
    public int rob(int[] nums) {
        if(nums.length == 1){
            return nums[0];
        }
        int[] dp = new int[nums.length];
        Arrays.fill(dp, -1);
        int take1 = solve(0, nums.length-1, nums, dp);
        Arrays.fill(dp, -1);
        int take2 = solve(1, nums.length, nums, dp);
        return Math.max(take1, take2);
    }
    public int solve(int ind, int e, int[] nums, int[] dp){
        if(ind >= e){
            return 0;
        }
        if(dp[ind] != -1){
            return dp[ind];
        }
        int take = nums[ind] + solve(ind+2, e, nums, dp);
        int notTake = solve(ind+1, e, nums, dp);
        return dp[ind] = Math.max(take, notTake);
    }
}
```