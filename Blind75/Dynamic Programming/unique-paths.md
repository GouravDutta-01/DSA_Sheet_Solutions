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
    public int uniquePaths(int m, int n) {
        int[][] dp = new int[m][n];
        for(int[] row : dp){
            Arrays.fill(row, -1);
        }
        return solve(0, 0, m, n, dp);
    }
    public int solve(int i, int j, int m, int n, int[][] dp){
        if(i == m-1 && j == n-1){
            return 1;
        }
        if(dp[i][j] != -1){
            return dp[i][j];
        }
        int count = 0;
        if(i+1 < m){
            count += solve(i+1, j, m, n, dp);
        }
        if(j+1 < n){
            count += solve(i, j+1, m, n, dp);
        }
        return dp[i][j] = count;
    }
}
```