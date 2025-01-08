# [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int findMin(int[] nums) {
        int low = 0;
        int high = nums.length-1;
        int mini = Integer.MAX_VALUE;
        while(low <= high){
            int mid = low + (high-low)/2;
            mini = Math.min(mini, nums[mid]);
            if(nums[low] <= nums[mid]){//left half sorted
                mini = Math.min(mini, nums[low]);
                low = mid+1;
            }
            else{//right half sorted
                mini = Math.min(mini, nums[mid]);
                high = mid-1;
            }
        }
        return mini;     
    }
}
```
### Note:
- Here, all values in the array are distinct.
- Find the sorted half then compare the minimum of the sorted half with the current minimum and remove the sorted half.