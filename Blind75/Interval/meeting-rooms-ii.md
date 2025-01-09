# [Meeting Rooms II](https://www.geeksforgeeks.org/problems/attend-all-meetings-ii/1)
**Difficulty:** Medium

### Solution 1 in Java
```java
class Solution {
    public int minMeetingRooms(int[] start, int[] end) {
        int maxVal = 0;
        for(int val : end){
            maxVal = Math.max(maxVal, val);
        }
        int[] line = new int[maxVal+1];
        for(int i=0; i<start.length; i++){
            line[start[i]]++;
            line[end[i]]--;
        }
        int currCount = 0;
        int maxMeetings = 0;//max meeting at a particular time
        for(int i=0; i<maxVal+1; i++){
            currCount += line[i];
            maxMeetings = Math.max(maxMeetings, currCount);
        }
        return maxMeetings;
    }
}
```

### Solution 2 in Java
```java
class Solution {
    public int minMeetingRooms(int[] start, int[] end) {
        Arrays.sort(start);
        Arrays.sort(end);
        int currCount = 0;
        int maxMeetings = 0;
        int i = 0;
        int j = 0;
        while(i < start.length && j < end.length){
            if(start[i] < end[j]){
                currCount++;
                i++;
            }
            else if(start[i] > end[j]){
                currCount--;
                j++;
            }
            else{
                i++;
                j++;
            }
            maxMeetings = Math.max(maxMeetings, currCount);
        }
        return maxMeetings;
    }
}
```

### Note:
- Here, we can't just find overall maximum non overlapping intervals. We need to find maximum overlap that can take place at a particular moment.The minimum room required corresponds to the maximum possible overlap that can occur at any point in time.