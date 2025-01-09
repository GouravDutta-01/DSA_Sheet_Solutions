# [Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int eraseOverlapIntervals(int[][] intervals) {
        int n = intervals.length;
        int count = 1;//count to store maximum non overlapping
        Arrays.sort(intervals, (a, b) -> a[1] - b[1]);
        int currEnd = intervals[0][1];
        for(int i=1; i<n; i++){
            if(intervals[i][0] >= currEnd){
                count++;
                currEnd = intervals[i][1];
            }
        }
        return n-count;    
    }
}
```
### Note:
- We sort in increasing order of end time as for maximum non overlapping intervals, we greedily take intervals with minimum end times first