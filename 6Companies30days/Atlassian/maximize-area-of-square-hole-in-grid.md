# [Maximize Area of Square Hole in Grid](https://leetcode.com/problems/maximize-area-of-square-hole-in-grid/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int maximizeSquareHoleArea(int n, int m, int[] hBars, int[] vBars) {
        Arrays.sort(hBars);
        Arrays.sort(vBars);
        int maxHCount = 1;
        int currHCount = 1;
        for(int i=1; i<hBars.length; i++){
            if(hBars[i] == hBars[i-1]+1){
                currHCount++;
            }
            else{
                currHCount = 1;
            }
            maxHCount = Math.max(maxHCount, currHCount);
        }
        int maxVCount = 1;
        int currVCount = 1;
        for(int i=1; i<vBars.length; i++){
            if(vBars[i] == vBars[i-1]+1){
                currVCount++;
            }
            else{
                currVCount = 1;
            }
            maxVCount = Math.max(maxVCount, currVCount);
        }
        int side = 1+Math.min(maxHCount, maxVCount);
        return side*side;
    }
}
```