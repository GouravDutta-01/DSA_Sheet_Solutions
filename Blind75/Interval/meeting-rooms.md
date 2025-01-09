# [Meeting Rooms](https://www.geeksforgeeks.org/problems/attend-all-meetings/0)
**Difficulty:** Easy

### Solution 1 in Java
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
### Solution 2 in Java
```java
class Solution {
    static boolean canAttend(int[][] arr) {
        Arrays.sort(arr, (a, b) -> a[1] - b[1]);
        int currEnd = arr[0][1];
        int count = 1;
        for(int i=1; i<arr.length; i++){
            if(arr[i][0] >= currEnd){
                currEnd = arr[i][1];
                count++;
            }
        }
        return count == arr.length;
    }
}
```