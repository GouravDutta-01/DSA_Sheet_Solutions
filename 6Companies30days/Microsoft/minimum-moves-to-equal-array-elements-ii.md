# [Minimum Moves to Equal Array Elements II](https://leetcode.com/problems/minimum-moves-to-equal-array-elements-ii/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int minMoves2(int[] nums) {
        Arrays.sort(nums);
        int n = nums.length;
        int count = 0;
        for(int i=0; i<n; i++){
            count += Math.abs(nums[i]-nums[n/2]);
        }
        return count;
    }
}
```
### Note :
- The median minimizes the sum of absolute differences by balancing the data on both sides, making it the optimal target for minimizing moves.

### Solution 2 in Java(Brute Force)
```java
class Solution {
    public int minMoves2(int[] nums) {
        long minMoves = Integer.MAX_VALUE;
        for(int i=0; i<nums.length; i++){
            long currMoves = 0;
            for(int j=0; j<nums.length; j++){
                currMoves += Math.abs(nums[i]-nums[j]);
            }
            minMoves = Math.min(minMoves, currMoves);
        }
        return (int)minMoves;   
    }
}
```

