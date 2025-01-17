# [Find the Distance Value Between Two Arrays](https://leetcode.com/problems/find-the-distance-value-between-two-arrays/)
**Difficulty:** Easy

### Solution in Java
```java
class Solution {
    public int findTheDistanceValue(int[] arr1, int[] arr2, int d) {
        Arrays.sort(arr2);
        int count = 0;
        for(int val : arr1){
            int from = val-d;
            int to = val+d;
            if(isValid(arr2, from, to)){
                count++;
            }
        }
        return count;   
    }
    public boolean isValid(int[] nums, int from, int to){//returns true if arr do not contain any element between range [from, to]
        int low = 0;
        int high = nums.length-1;
        while(low <= high){
            int mid = low + (high-low)/2;
            if(nums[mid] >= from && nums[mid] <= to){
                return false;
            }
            else if(nums[mid] < from){//need to increase low as all index less than mid are also in valid range
                low = mid+1;
            }
            else if(nums[mid] > to){//need to decrease high as all index greater than mid are also in valid range
                high = mid-1;
            }
        }
        return true;
    }
}
```