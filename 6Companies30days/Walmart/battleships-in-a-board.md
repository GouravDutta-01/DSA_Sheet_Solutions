# [Battleships in a Board](https://leetcode.com/problems/battleships-in-a-board/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int countBattleships(char[][] board) {
        int m = board.length;
        int n = board[0].length;
        boolean[][] vis = new boolean[m][n];
        int[][] directions = new int[][]{{0, 1}, {0, -1}, {1, 0}, {-1, 0}};
        int count = 0;
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if(!vis[i][j] && board[i][j] == 'X'){
                    dfs(i, j, board, vis, directions);
                    count++;
                }
            }
        }
        return count;
    }
    public void dfs(int i, int j, char[][] board, boolean[][] vis, int[][] directions){
        vis[i][j] = true;
        for(int[] direction : directions){
            int r = i + direction[0];
            int c = j + direction[1];
            if(r >= 0 && c >= 0 && r < board.length && c < board[0].length && !vis[r][c] && board[r][c] == 'X'){
                dfs(r, c, board, vis, directions);
            }
        }
    }
}
```
