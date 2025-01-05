# [Pacific Atlantic Water Flow](https://leetcode.com/problems/pacific-atlantic-water-flow/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public List<List<Integer>> pacificAtlantic(int[][] heights) {
        int m = heights.length;
        int n = heights[0].length;
        boolean[][] pacificVis = new boolean[m][n];
        boolean[][] atlanticVis = new boolean[m][n];
        int[][] directions = new int[][]{{0, 1}, {0, -1}, {1, 0}, {-1, 0}};
        for(int i=0; i<m; i++){
            dfs(i, 0, pacificVis, heights, directions, m, n);
            dfs(i, n-1, atlanticVis, heights, directions, m, n);
        }
       for(int j=0; j<n; j++){
            dfs(0, j, pacificVis, heights, directions, m, n);
            dfs(m-1, j, atlanticVis, heights, directions, m, n);
        }
        List<List<Integer>> result = new ArrayList<>();
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if(pacificVis[i][j] && atlanticVis[i][j]){
                    result.add(Arrays.asList(i, j));
                }
            }
        }
        return result;
    }
    public void dfs(int i, int j, boolean[][] vis, int[][] heights, int[][] directions, int m, int n){
        vis[i][j] = true;
        for(int[] direction : directions){
            int r = i + direction[0];
            int c = j + direction[1];
            if(r >= 0 && c >= 0 && r < m && c < n && !vis[r][c] && heights[r][c] >= heights[i][j]){
                dfs(r, c, vis, heights, directions, m, n);
            }
        }
    }
}
```
