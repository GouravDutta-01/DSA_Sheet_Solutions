# [Insert Interval](https://leetcode.com/problems/insert-interval/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int[][] insert(int[][] intervals, int[] newInterval) {
        ArrayList<int[]> mergedList = new ArrayList<>();
        int i = 0;
        while(i < intervals.length){
            if(intervals[i][1] < newInterval[0]){//new interval afterwards
                mergedList.add(intervals[i]);
                i++;
            }
            else if(intervals[i][0] > newInterval[1]){//new interval before current interval
                break;
            }
            else{//overlap between new and current interval
                newInterval[0] = Math.min(intervals[i][0], newInterval[0]);
                newInterval[1] = Math.max(intervals[i][1], newInterval[1]);
                i++;
            }
        }
        mergedList.add(newInterval);
        while(i < intervals.length){
            mergedList.add(intervals[i]);
            i++;
        }
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
