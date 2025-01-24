# [Minimum Number of Days to Disconnect Island](https://leetcode.com/problems/minimum-number-of-days-to-disconnect-island/)
**Difficulty:** Hard

### Solution in Java
```java
class Solution {
    public int minDays(int[][] grid) {
        int m = grid.length;
        int n = grid[0].length;
        int[][] directions = new int[][]{{1, 0}, {-1, 0}, {0, 1}, {0, -1}};
        boolean[][] vis = new boolean[m][n];
        int count = 0;
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if(!vis[i][j] && grid[i][j] == 1){
                    dfs(i, j, grid, vis, directions);
                    count++;
                }
            }
        } 
        if(count != 1){
            return 0;
        }
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if(grid[i][j] == 1){
                    count = 0;
                    grid[i][j] = 0;
                    for(boolean[] row : vis){
                        Arrays.fill(row, false);
                    }
                    for(int k=0; k<m; k++){
                        for(int l=0; l<n; l++){
                            if(!vis[k][l] && grid[k][l] == 1){
                                dfs(k, l, grid, vis, directions);
                                count++;
                            }
                        }
                    }
                    if(count != 1){
                        return 1;
                    }
                    grid[i][j] = 1;
                }
            }
        } 
        return 2; 
    }
    public void dfs(int i, int j, int[][] grid, boolean[][] vis, int[][] directions){
        vis[i][j] = true;
        for(int[] direction : directions){
            int r = i + direction[0];
            int c = j + direction[1];
            if(r >= 0 && c >= 0 && r < grid.length && c < grid[0].length && !vis[r][c] && grid[r][c] == 1){
                dfs(r, c, grid, vis, directions);
            }
        }
    }
}
```
