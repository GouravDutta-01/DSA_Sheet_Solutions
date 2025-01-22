# [Map of Highest Peak](https://leetcode.com/problems/map-of-highest-peak/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int[][] highestPeak(int[][] isWater) {
        int m = isWater.length;
        int n = isWater[0].length;
        int[][] ans = new int[m][n];
        Queue<int[]> q = new LinkedList<>();
        boolean[][] vis = new boolean[m][n];
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                if(isWater[i][j] == 1){//start bfs from all 1's for finding distance of nearest cell that contains 1
                    q.add(new int[]{i, j});
                    vis[i][j] = true;
                }
            }
        }
        int[][] directions = new int[][]{{0, 1}, {0, -1}, {1, 0}, {-1, 0}};
        int level = 0;
        while(!q.isEmpty()){
            int size = q.size();
            while(size-- > 0){
                int[] curr = q.poll();
                int x = curr[0];
                int y = curr[1];
                ans[x][y] = level;
                for(int[] direction : directions){
                    int r = x + direction[0];
                    int c = y + direction[1];
                    if(r >= 0 && c >= 0 && r < m && c < n && !vis[r][c] && isWater[r][c] == 0){
                        isWater[r][c] = 1;
                        vis[r][c] = true;
                        q.add(new int[]{r, c});
                    }
                }

            }
            if(!q.isEmpty()){
                level++;
            }
        }
        return ans;
    }
}
```