# [Valid Sudoku](https://leetcode.com/problems/valid-sudoku/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public boolean isValidSudoku(char[][] board) {
        for (int i=0; i<9; i++) {
            HashSet<Character> setRow = new HashSet<>();// for checking distinct value in each row
            HashSet<Character> setCol = new HashSet<>();// for checking distinct value in each column
            for (int j=0; j<9; j++) {
                if (setRow.contains(board[i][j]) || setCol.contains(board[j][i])) {
                    return false;
                }
                if(board[i][j] != '.'){
                    setRow.add(board[i][j]);
                }
                if(board[j][i] != '.'){
                    setCol.add(board[j][i]);
                }
            }
        }
        for (int i=0; i<3; i++) {
            for (int j=0; j<3; j++) {
                HashSet<Character> set = new HashSet<>();// for checking distinct value in each subgrid
                for (int k=0; k<9; k++) {
                    int r = 3*i + k/3;
                    int c = 3*j + k%3;
                    if (set.contains(board[r][c])) {
                        return false;
                    }
                    if(board[r][c] != '.'){
                        set.add(board[r][c]);
                    }
                }
            }
        }
        return true;
    }
}
```
