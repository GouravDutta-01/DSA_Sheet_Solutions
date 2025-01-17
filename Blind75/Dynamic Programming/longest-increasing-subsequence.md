# [Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/)
**Difficulty:** Medium

### Solution 1 in Java(Space Optimization)
```java

```
### Solution 2 in Java(Tabulation)
```java
class Solution {
    public int longestCommonSubsequence(String text1, String text2) {
        int m = text1.length();
        int n = text2.length();
        int[][] dp = new int[m+1][n+1];//dp[i][j] represents length of LCS of first i characters of text1 and first j characters of text2
        for(int i=1; i<=m; i++){
            for(int j=1; j<=n; j++){
                if(text1.charAt(i-1) == text2.charAt(j-1)){
                    dp[i][j] = 1 + dp[i-1][j-1];
                }
                else{
                    dp[i][j] = Math.max(dp[i-1][j], dp[i][j-1]);
                }
            }
        }
        return dp[m][n];
    }
}
```
### Solution 3 in Java(Memoization)
```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        int[][] dp = new int[nums.length][nums.length+1];
        for(int[] row : dp){
            Arrays.fill(row, -1);
        }
        return solve(0, -1, nums, dp);
    }
    public int solve(int ind, int prevInd, int[] nums, int[][] dp){
        if(ind == nums.length){
            return 0;
        }
        if(dp[ind][prevInd+1] != -1){
            return dp[ind][prevInd+1];
        }
        int take = -(int)1e9;
        if(prevInd == -1 || nums[ind] > nums[prevInd]){
            take = 1 + solve(ind+1, ind, nums, dp);
        }
        int notTake = solve(ind+1, prevInd, nums, dp);
        return dp[ind][prevInd+1] = Math.max(take, notTake);  
    }
}
```