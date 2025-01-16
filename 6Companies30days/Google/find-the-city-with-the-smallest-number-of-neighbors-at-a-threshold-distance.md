# [Find the City With the Smallest Number of Neighbors at a Threshold Distance](https://leetcode.com/problems/find-the-city-with-the-smallest-number-of-neighbors-at-a-threshold-distance/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int findTheCity(int n, int[][] edges, int distanceThreshold) {
        int[][] adjMatrix = new int[n][n];
        for(int i=0; i<n; i++){
            for(int j=0; j<n; j++){
                if(i == j){
                    adjMatrix[i][j] = 0;
                }
                else{
                    adjMatrix[i][j] = (int)1e9;
                }
            }
        }
        for(int[] edge : edges){
            int u = edge[0];
            int v = edge[1];
            int wt = edge[2];
            adjMatrix[u][v] = Math.min(adjMatrix[u][v], wt);
            adjMatrix[v][u] = Math.min(adjMatrix[v][u], wt);
        }
        for(int via=0; via<n; via++){
            for(int i=0; i<n; i++){
                for(int j=0; j<n; j++){
                    adjMatrix[i][j] = Math.min(adjMatrix[i][j], adjMatrix[i][via] + adjMatrix[via][j]);
                }
            }
        }
        int mini = Integer.MAX_VALUE;
        int ans = -1;
        for(int i=0; i<n; i++){
            int count = 0;
            for(int distance : adjMatrix[i]){
                if(distance <= distanceThreshold){
                    count++;
                }
            }
            if(count <= mini){
                ans = i;
                mini = count;
            }
        }
        return ans;     
    }
}
```
