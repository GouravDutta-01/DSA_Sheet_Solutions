# [Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int search(int[] nums, int target) {
        int low = 0;
        int high = nums.length-1;
        while(low <= high){
            int mid = low + (high-low)/2;
            if(nums[mid] == target){
                return mid;
            }
            if(nums[low] <= nums[mid]){//left half sorted
                if(target >= nums[low] && target < nums[mid]){
                    high = mid-1;
                }
                else{
                    low = mid+1;
                }
            }
            else{//right half sorted
                if(target > nums[mid] && target <= nums[high]){
                    low = mid+1;
                }
                else{
                    high = mid-1;
                }
            }
        }
        return -1;    
    }
}
```
### Note:
- Here, all values in the array are distinct.
- Find the sorted half and then search if the target is within the sorted half range.