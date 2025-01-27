# [Construct the Longest New String](https://leetcode.com/problems/construct-the-longest-new-string/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int longestString(int x, int y, int z) {
        int[][][][] dp = new int[4][x+1][y+1][z+1];
        for(int[][][] temp1 : dp){
            for(int[][] temp2 : temp1){
                for(int[] temp3 : temp2){
                    Arrays.fill(temp3, -1);
                }
            }
        }
        return solve(-1, x, y, z, dp);
    }
    public int solve(int prev, int x, int y, int z, int[][][][] dp){
        if(x == 0 && y == 0 && z == 0){
            return 0;
        }
        if(dp[prev+1][x][y][z] != -1){
            return dp[prev+1][x][y][z];
        }
        int count = 0;
        if(prev == -1){
            if(x > 0){
                count = 2+solve(0, x-1, y, z, dp);
            }
            if(y > 0){
                count = Math.max(count, 2+solve(1, x, y-1, z, dp));
            }
            if(z > 0){
                count = Math.max(count, 2+solve(2, x, y, z-1, dp));
            }
        }
        else if(prev == 0){
            if(y > 0){
                count = 2+solve(1, x, y-1, z, dp);
            }
        }
        else if(prev == 1){
            if(z > 0){
                count = 2+solve(2, x, y, z-1, dp);
            }
            if(x > 0){
                count = Math.max(count, 2+solve(0, x-1, y, z, dp));
            }
        }
        else{
            if(x > 0){
                count = 2+solve(0, x-1, y, z, dp);
            }
            if(z > 0){
                count = Math.max(count, 2+solve(2, x, y, z-1, dp));
            }
        }
        return dp[prev+1][x][y][z] = count;
    }
}
```
