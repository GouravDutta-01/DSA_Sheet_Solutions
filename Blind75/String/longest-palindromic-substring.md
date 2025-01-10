# [Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public String longestPalindrome(String s) {
        int n = s.length();
        int maxLen = Integer.MIN_VALUE;
        int startInd = -1;
        boolean[][] dp = new boolean[n][n];//dp[i][j] denotes if substring(i...j) is a palindrome or not
        for(int len=1; len<=n; len++){
            for(int i=0; len+i-1<n; i++){
                int j = len+i-1;
                if(len == 1){
                    dp[i][j] = true;
                }
                else if(len == 2){
                    dp[i][j] = (s.charAt(i) == s.charAt(j));
                }
                else{
                    dp[i][j] = (s.charAt(i) == s.charAt(j)) && dp[i+1][j-1];
                }
                if(dp[i][j] && j-i+1 > maxLen){
                    maxLen = j-i+1;
                    startInd = i;
                }
            }
        }
        return s.substring(startInd, startInd+maxLen);  
    }
}
```
