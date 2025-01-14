# [Word Break](https://leetcode.com/problems/word-break/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public boolean wordBreak(String s, List<String> wordDict) {
        HashSet<String> set = new HashSet<>();
        for(String word : wordDict){
            set.add(word);
        }
        int[] dp = new int[s.length()];
        Arrays.fill(dp, -1);
        return solve(0, s, set, dp) == 1 ? true : false;    
    }
    public int solve(int ind, String s, HashSet<String> set, int[] dp){
        if(ind >= s.length()){
            return 1;
        }
        if(set.contains(s.substring(ind, s.length()))){
            return 1;
        }
        if(dp[ind] != -1){
            return dp[ind];
        }
        for(int len=1; len<=s.length()-ind; len++){
            if(((set.contains(s.substring(ind, ind+len)) ? 1 : 0) & solve(ind+len, s, set, dp)) == 1){
                return dp[ind] = 1;
            }
        }
        return dp[ind] = 0;
    }
}
```
