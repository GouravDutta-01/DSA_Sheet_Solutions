# [Find in Mountain Array](https://leetcode.com/problems/find-in-mountain-array/)
**Difficulty:** Hard

### Solution in Java
```java
/**
 * // This is MountainArray's API interface.
 * // You should not implement it, or speculate about its implementation
 * interface MountainArray {
 *     public int get(int index) {}
 *     public int length() {}
 * }
 */
class Solution {
    public int findInMountainArray(int target, MountainArray mountainArr) {
        int n = mountainArr.length();
        int mountainInd = solve(mountainArr, n);
        int minInd = binarySearchInc(0, mountainInd, mountainArr, target);
        if(minInd != -1){
            return minInd;
        }
        minInd = binarySearchDec(mountainInd+1, n-1, mountainArr, target);
        return minInd;
    }
    public int binarySearchInc(int low, int high, MountainArray mountainArr, int target){
        int ans = -1;
        while(low <= high){
            int mid = low + (high-low)/2;
            int midVal = mountainArr.get(mid);
            if(midVal == target){
                ans = mid;
                high = mid-1;
            }
            else if(midVal > target){
                high = mid-1;
            }
            else{
                low = mid+1;
            }
        }
        return ans;
    }
    public int binarySearchDec(int low, int high, MountainArray mountainArr, int target){
        int ans = -1;
        while(low <= high){
            int mid = low + (high-low)/2;
            int midVal = mountainArr.get(mid);
            if(midVal == target){
                ans = mid;
                high = mid-1;
            }
            else if(midVal > target){
                low = mid+1;
            }
            else{
                high = mid-1;
            }
        }
        return ans;
    }
    public int solve(MountainArray mountainArr, int n){
        int low = 1;
        int high = n-2;
        while(low <= high){
            int mid = low + (high-low)/2;
            int midVal = mountainArr.get(mid);
            if(midVal > mountainArr.get(mid-1) && midVal > mountainArr.get(mid+1)){
                return mid;
            }
            if(midVal > mountainArr.get(mid-1)){
                low = mid+1;
            }
            else if(midVal > mountainArr.get(mid+1)){
                high = mid-1;
            }
        }
        return -1;
    }
}
```
