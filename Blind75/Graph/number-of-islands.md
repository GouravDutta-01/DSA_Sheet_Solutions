# [Number of Islands](https://leetcode.com/problems/number-of-islands/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int numIslands(char[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        boolean[][] vis = new boolean[m][n];
        int[][] directions = new int[][]{{0, 1}, {0, -1}, {1, 0}, {-1, 0}};
        int count = 0;
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if(grid[i][j] == '1' && !vis[i][j]){
                    dfs(i, j, vis, grid, directions, m, n);
                    count++;
                }
            }
        }
        return count;    
    }
    public void dfs(int i, int j, boolean[][] vis, char[][] grid, int[][] directions, int m, int n){
        vis[i][j] = true;
        for(int[] direction : directions){
            int r = i + direction[0];
            int c = j + direction[1];
            if(r >= 0 && c >= 0 && r < m && c < n && !vis[r][c] && grid[r][c] == '1'){
                dfs(r, c, vis, grid, directions, m, n);
            }
        }
    }
}
```
