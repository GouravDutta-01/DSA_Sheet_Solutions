# [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int[] prefix = new int[n];
        int[] suffix = new int[n];
        prefix[0] = nums[0];
        suffix[n-1] = nums[n-1];
        for(int i=1; i<n; i++){
            prefix[i] = nums[i]*prefix[i-1];
            suffix[n-i-1] = nums[n-i-1]*suffix[n-i];
        }
        int[] answer = new int[n];
        answer[0] = suffix[1];
        answer[n-1] = prefix[n-2];
        for(int i=1; i<n-1; i++){
            answer[i] = suffix[i+1]*prefix[i-1];
        }
        return answer;
    }
}
```
