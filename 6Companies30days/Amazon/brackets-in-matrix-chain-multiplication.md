# [Brackets in Matrix Chain Multiplication](https://www.geeksforgeeks.org/problems/brackets-in-matrix-chain-multiplication1024/1)
**Difficulty:** Hard

### Solution 1 in Java (Memoization)
```java
class Pair{
    int count;
    String str;
    public Pair(int count, String str){
        this.count = count;
        this.str = str;
    }
}
class Solution {
    static String matrixChainOrder(int arr[]) {
        Pair[][] dp = new Pair[arr.length][arr.length];
        for(int i=0; i<dp.length; i++){
            for(int j=0; j<dp[0].length; j++){
                dp[i][j] = new Pair(-1, "");
            }
        }
        return solve(1, arr.length-1, arr, dp).str;
    }
    static Pair solve(int i, int j, int[] arr, Pair[][] dp){
        if(i == j){
            return new Pair(0, String.valueOf((char)('A'+i-1)));
        }
        if(dp[i][j].count != -1){
            return dp[i][j];
        }
        int mini = Integer.MAX_VALUE;
        String s = "";
        for(int k=i; k<j; k++){
            Pair left = solve(i, k, arr, dp);
            Pair right = solve(k+1, j, arr, dp);
            if(arr[i-1]*arr[k]*arr[j] + left.count + right.count < mini){
                mini = arr[i-1]*arr[k]*arr[j] + left.count + right.count;
                s = "(" + left.str + right.str + ")";
            }
        }
        return dp[i][j] = new Pair(mini, s);
    }
}
```
