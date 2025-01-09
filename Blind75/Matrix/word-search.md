# [Word Search](https://leetcode.com/problems/word-search/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public boolean exist(char[][] board, String word) {
        int m = board.length;
        int n = board[0].length;
        int[][] directions = new int[][]{{0, 1}, {0, -1}, {1, 0}, {-1, 0}};
        boolean[][] vis = new boolean[m][n];
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if(board[i][j] == word.charAt(0)){
                    if(dfs(i, j, 1, board, word, vis, directions)){
                        return true;
                    }
                }
            }
        }
        return false;
    }
    public boolean dfs(int i, int j, int ind, char[][] board, String word, boolean[][] vis, int[][] directions){
        if(ind == word.length()){
            return true;
        }
        vis[i][j] = true;
        for(int[] direction : directions){
            int r = i + direction[0];
            int c = j + direction[1];
            if(r >= 0 && c >= 0 && r < board.length && c < board[0].length && !vis[r][c] && board[r][c] == word.charAt(ind)){
                if(dfs(r, c, ind+1, board, word, vis, directions)){
                    return true;
                }
            }
        }
        vis[i][j] = false;//backtrack
        return false;
    }
}
```
