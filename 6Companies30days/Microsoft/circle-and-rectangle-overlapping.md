# [Circle and Rectangle Overlapping](https://leetcode.com/problems/circle-and-rectangle-overlapping/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public boolean checkOverlap(int radius, int xCenter, int yCenter, int x1, int y1, int x2, int y2) {
        int xMin = Math.max(x1, Math.min(x2, xCenter));//nearest x-coordinate to the center of circle present on rectangle
        int yMin = Math.max(y1, Math.min(y2, yCenter));//nearest y-coordinate to the center of circle present on rectangle
        int dSquared = (xMin-xCenter)*(xMin-xCenter) + (yMin-yCenter)*(yMin-yCenter);//square of distance between the nearest point on rectangle and the center of circle
        return radius*radius >= dSquared;      
    }
}
```
