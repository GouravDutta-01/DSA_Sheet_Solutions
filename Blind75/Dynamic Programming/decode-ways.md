# [Decode Ways](https://leetcode.com/problems/decode-ways/)
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
    public int numDecodings(String s) {
        int[] dp = new int[s.length()];
        Arrays.fill(dp, -1);
        return solve(0, s, dp);
    }
    public int solve(int ind, String s, int[] dp){
        if(ind == s.length()){
            return 1;
        }
        if(s.charAt(ind) == '0'){
            return 0;
        }
        if(dp[ind] != -1){
            return dp[ind];
        }
        int count = 0;
        count += solve(ind+1, s, dp);//taking starting character
        if(ind+1 < s.length()){//taking starting 2 characters
            if(s.charAt(ind) == '1' || (s.charAt(ind) == '2' && s.charAt(ind+1)-'0' <= 6)){
                count += solve(ind+2, s, dp);
            }
        }
        return dp[ind] = count;
    }
}
```