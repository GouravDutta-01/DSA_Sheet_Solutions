# [Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/)
**Difficulty:** Medium

### Solution 1 in Java
```java
class Solution {
    public void setZeroes(int[][] matrix) {
        int m = matrix.length;
        int n = matrix[0].length;
        int[] row = new int[m];
        int[] col = new int[n];
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if(matrix[i][j] == 0){
                    row[i] = -1;
                    col[j] = -1;
                }
            }
        }
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if(row[i] == -1 || col[j] == -1){
                    matrix[i][j] = 0;
                }
            }
        }
    }
}
```
### Solution 2 in Java
```java
class Solution {
    public void setZeroes(int[][] matrix) {
        int m = matrix.length;
        int n = matrix[0].length;
        int col0 = 1;//for 0th col as we are already using matrix[0][0] for 0th row
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if(matrix[i][j] == 0){
                    matrix[i][0] = 0;//marking ith row 
                    if(j == 0){
                        col0 = 0;
                    }
                    else{
                        matrix[0][j] = 0;//marking jth col
                    }
                }
            }
        }
        for(int i=1; i<m; i++){
            for(int j=1; j<n; j++){
                if(matrix[i][0] == 0 || matrix[0][j] == 0){
                    matrix[i][j] = 0;
                }
            }
        }
        if(matrix[0][0] == 0){//mark the 0th row first as if we first check col0, then if col0 == 0, it will mark matrix[0][0] as 0 which will cause error
            for(int j=0; j<n; j++){
                matrix[0][j] = 0;
            }
        }
        if(col0 == 0){
            for(int i=0; i<m; i++){
                matrix[i][0] = 0;
            }
        }
    }
}
```
