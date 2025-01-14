# [Extra Characters in a String](https://leetcode.com/problems/extra-characters-in-a-string/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int minExtraChar(String s, String[] dictionary) {
        HashSet<String> set = new HashSet<>();
        for(String dict : dictionary){
            set.add(dict);
        }
        int[] dp = new int[s.length()];
        Arrays.fill(dp, -1);
        return solve(0, s, set, dp);
    }
    public int solve(int ind, String s, HashSet<String> set, int[] dp){
        if(ind >= s.length()){
            return 0;
        }
        if(set.contains(s.substring(ind, s.length()))){
            return 0;
        }
        if(dp[ind] != -1){
            return dp[ind];
        }
        int mini = Integer.MAX_VALUE;
        for(int len=1; len<=s.length()-ind; len++){
            if(set.contains(s.substring(ind, ind+len))){
                mini = Math.min(mini, solve(ind+len, s, set, dp));
            }
            else{
                mini = Math.min(mini, 1 + solve(ind+1, s, set, dp));
            }
        }
        return dp[ind] = mini;
    }
}
```
