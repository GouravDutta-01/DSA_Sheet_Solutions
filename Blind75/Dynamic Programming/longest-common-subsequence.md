# [Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/)
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
    public int longestCommonSubsequence(String text1, String text2) {
        int[][] dp = new int[text1.length()][text2.length()];
        for(int[] row : dp){
            Arrays.fill(row, -1);
        }
        return solve(0, 0, text1, text2, dp);
    }
    public int solve(int i, int j, String text1, String text2, int[][] dp){
        if(i == text1.length() || j == text2.length()){
            return 0;
        }
        if(dp[i][j] != -1){
            return dp[i][j];
        }
        int take = -(int)1e9;
        if(text1.charAt(i) == text2.charAt(j)){
            take = 1 + solve(i+1, j+1, text1, text2, dp);
        }
        int notTake = Math.max(solve(i+1, j, text1, text2, dp), solve(i, j+1, text1, text2, dp));
        return dp[i][j] = Math.max(take, notTake);
    }
}
```