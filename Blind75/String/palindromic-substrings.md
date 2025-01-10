# [Palindromic Substrings](https://leetcode.com/problems/palindromic-substrings/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int countSubstrings(String s) {
        int n = s.length();
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
            }
        }
        int count = 0;
        for(int i=0; i<n; i++){
            for(int j=i; j<n; j++){
                if(dp[i][j] == true){
                    count++;
                }
            }
        }
        return count;    
    }
}
```
