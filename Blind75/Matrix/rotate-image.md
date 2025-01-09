# [Rotate Image](https://leetcode.com/problems/rotate-image/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public void rotate(int[][] matrix) {
        int n = matrix.length;
        for(int i=0; i<n; i++){//Transpose of matrix
            for(int j=0; j<i; j++){
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }
        for(int[] row : matrix){
            reverse(row);
        }    
    }
    public void reverse(int[] arr){
        int i = 0;
        int j = arr.length-1;
        while(i < j){
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
            i++;
            j--;
        }
    }
}
```
