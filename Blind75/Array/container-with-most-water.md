# [Container With Most Water](https://leetcode.com/problems/container-with-most-water/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int maxArea(int[] height) {
        int l = 0;
        int r = height.length-1;
        int maxWater = 0;
        while(l < r){
            maxWater = Math.max(maxWater, Math.min(height[l], height[r])*(r-l));
            if(height[l] < height[r]){
                l++;
            }
            else if(height[l] >= height[r]){
                r--;
            }
        }
        return maxWater;
    }
}
```
### Note:
- We are using a greedy approach here.
- At each step, we are moving that pointer which has minimum height expecting a higher height for storing more water.
