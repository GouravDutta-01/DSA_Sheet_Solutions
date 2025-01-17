# [Word Break](https://leetcode.com/problems/word-break/)
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
    public boolean wordBreak(String s, List<String> wordDict) {
        HashSet<String> set = new HashSet<>();
        for(String val : wordDict){
            set.add(val);
        }
        Boolean[] dp = new Boolean[s.length()];//dp[i] returns true if substring of s starting from ith index to end belongs to wordDict
        return solve(0, s, set, dp);
    }
    public boolean solve(int ind, String s, HashSet<String> set, Boolean[] dp){
        if(ind == s.length()){
            return true;
        }
        if(set.contains(s.substring(ind, s.length()))){
            return true;
        }
        if(dp[ind] != null){
            return dp[ind];
        }
        for(int i=ind; i<s.length(); i++){
            if(set.contains(s.substring(ind, i+1)) && solve(i+1, s, set, dp)){
                return dp[ind] = true;
            }
        }
        return dp[ind] = false;
    }
}
```