# [Merge Intervals](https://leetcode.com/problems/merge-intervals/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int[][] merge(int[][] intervals) {
        Arrays.sort(intervals, (a, b) -> a[0] - b[0]);
        ArrayList<int[]> mergedList = new ArrayList<>();
        int i = 1;
        while(i < intervals.length){
            if(intervals[i][0] > intervals[i-1][1]){//no overlap
                mergedList.add(intervals[i-1]);
                i++;
            }
            else{//overlap
                intervals[i][0] = Math.min(intervals[i][0], intervals[i-1][0]);
                intervals[i][1] = Math.max(intervals[i][1], intervals[i-1][1]);
                i++;
            }
        }
        mergedList.add(intervals[i-1]);
        int[][] ans = new int[mergedList.size()][2];
        int ind = 0;
        for(int[] val : mergedList){
            ans[ind][0] = val[0];
            ans[ind][1] = val[1];
            ind++;
        }
        return ans;
    }
}
```
