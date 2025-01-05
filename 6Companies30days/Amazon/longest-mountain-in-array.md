# [Longest Mountain in Array](https://leetcode.com/problems/longest-mountain-in-array/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int longestMountain(int[] arr) {
        int n = arr.length;
        int[] prefix = new int[n];//longest increasing subarray length ending at index i
        int[] suffix = new int[n];//longest decreasing subarray length starting at index i
        prefix[0] = 1;
        suffix[n-1] = 1;
        for(int i=1; i<n; i++){
            if(arr[i] > arr[i-1]){
                prefix[i] = 1+prefix[i-1];
            }
            else{
                prefix[i] = 1;
            }
        }
        for(int i=n-2; i>=0; i--){
            if(arr[i] > arr[i+1]){
                suffix[i] = 1+suffix[i+1];
            }
            else{
                suffix[i] = 1;
            }
        }
        int maxLen = 0;
        for(int i=1; i<n-1; i++){
            if(prefix[i] > 1 && suffix[i] > 1){//for valid subarray
                maxLen = Math.max(maxLen, prefix[i]+suffix[i]-1);
            }
        }
        return maxLen;   
    }
}
```
