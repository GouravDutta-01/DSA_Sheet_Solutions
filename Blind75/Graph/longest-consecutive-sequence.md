# [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int longestConsecutive(int[] nums) {
        HashSet<Integer> set = new HashSet<>();
        for(int val : nums){
            set.add(val);
        }
        int maxLen = 0;
        for(int val : set){
            if(!set.contains(val-1)){//to make sure that we start from the starting point of the possible consecutive sequence
                int currLen = 1;
                int req = val+1;
                while(set.contains(req)){
                    currLen++;
                    req++;
                }
                maxLen = Math.max(maxLen, currLen);
            }
        }
        return maxLen;
    }
}
```
