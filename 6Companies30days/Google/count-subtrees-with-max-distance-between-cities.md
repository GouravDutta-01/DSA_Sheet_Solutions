# [Count Subtrees With Max Distance Between Cities](https://leetcode.com/problems/count-subtrees-with-max-distance-between-cities/)
**Difficulty:** Hard

### Solution in Java
```java
class Solution {
    public int[] countSubgraphsForEachDiameter(int n, int[][] edges) {
        int[] ans = new int[n-1];
        int[][] adjMat = new int[n][n];
        for(int[] row : adjMat){
            Arrays.fill(row, 100);
        }
        for(int[] edge : edges){
            int u = edge[0];
            int v = edge[1];
            adjMat[u-1][v-1] = 1;
            adjMat[v-1][u-1] = 1;
        }
        for(int via=0; via<n; via++){
            for(int i=0; i<n; i++){
                for(int j=0; j<n; j++){
                    adjMat[i][j] = Math.min(adjMat[i][j], adjMat[i][via] + adjMat[via][j]);
                }
            }
        }
        for(int i=0; i<(1<<n); i++){//trying all possible subsets
            int count = solve(i, adjMat, n);
            if(count > 0){
                ans[count-1]++;
            }
        }
        return ans;
    }
    public int solve(int subtree, int[][] adjMat, int n){
        int countNodes = 0;
        int countEdges = 0;
        int maxDist = 0;
        for(int i=0; i<n; i++){
            if(((1<<i)&subtree) == 0){//checking if ith node is in subtree or not
                continue;
            }
            countNodes++;
            for(int j=i+1; j<n; j++){
                if(((1<<j)&subtree) == 0){//checking if jth node is in subtree or not
                    continue;
                }
                if(adjMat[i][j] == 1){//if i and j directly connected then it's a edge
                    countEdges++;
                }
                maxDist = Math.max(maxDist, adjMat[i][j]);
            }
        }
        return (countNodes == countEdges+1) ? maxDist : 0;//returns maximum diameter if valid subtree
    }
}
```
