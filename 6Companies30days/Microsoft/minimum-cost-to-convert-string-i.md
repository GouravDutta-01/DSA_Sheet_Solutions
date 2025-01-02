# [Minimum Cost to Convert String I](https://leetcode.com/problems/minimum-cost-to-convert-string-i/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public long minimumCost(String source, String target, char[] original, char[] changed, int[] cost) {
        long[][] adjMatrix = new long[26][26];
        for(int i=0; i<26; i++){
            for(int j=0; j<26; j++){
                if(i != j){
                    adjMatrix[i][j] = Integer.MAX_VALUE;
                }
            }
        }
        for(int i=0; i<original.length; i++){
            int u = original[i]-'a';
            int v = changed[i]-'a';
            int wt = cost[i];
            adjMatrix[u][v] = Math.min(adjMatrix[u][v], wt);//Same mapping may be present with different costs, so we take min cost
        }
        for(int via=0; via<26; via++){
            for(int i=0; i<26; i++){
                for(int j=0; j<26; j++){
                    adjMatrix[i][j] = Math.min(adjMatrix[i][j], (long)adjMatrix[i][via] + adjMatrix[via][j]);
                }
            }
        }
        long minCost = 0;
        for(int i=0; i<source.length(); i++){
            int u = source.charAt(i)-'a';
            int v = target.charAt(i)-'a';
            if(adjMatrix[u][v] == Integer.MAX_VALUE){
                return -1;
            }
            minCost += adjMatrix[u][v];
        }
        return minCost;
    }
}
```
