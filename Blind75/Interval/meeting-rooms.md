# [Meeting Rooms](https://www.geeksforgeeks.org/problems/attend-all-meetings/0)
**Difficulty:** Easy

### Solution in Java
```java
class Solution {
    static boolean canAttend(int[][] arr) {
        Arrays.sort(arr, (a, b) -> a[0] - b[0]);
        int i = 1;
        while(i < arr.length){
            if(!(arr[i][0] >= arr[i-1][1])){
                return false;
            }
            i++;
        }
        return true;
    }
}
```
