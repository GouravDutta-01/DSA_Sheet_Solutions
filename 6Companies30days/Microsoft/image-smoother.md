# [Image Smoother](https://leetcode.com/problems/image-smoother/description/)
**Difficulty:** Easy

### Solution in Java
```java
class Solution {
    public int[][] imageSmoother(int[][] img) {
        int m = img.length;
        int n = img[0].length;
        int[][] ans = new int[m][n];
        int[][] directions = new int[][]{{1, 0}, {-1, 0}, {0, 1}, {0, -1}, {1, 1}, {-1, -1}, {-1, 1}, {1, -1}};
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                int size = 1;
                int sum = img[i][j];
                for(int[] direction : directions){
                    int r = i + direction[0];
                    int c = j + direction[1];
                    if(r >= 0 && c >= 0 && r < m && c < n){
                        sum += img[r][c];
                        size++;
                    }
                }
                ans[i][j] = sum/size;
            }
        } 
        return ans; 
    }
}
```
