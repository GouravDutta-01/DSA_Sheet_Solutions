# [Get Equal Substrings Within Budget](https://leetcode.com/problems/get-equal-substrings-within-budget/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int equalSubstring(String s, String t, int maxCost) {
        int left = 0;
        int right = 0;
        int maxLen = 0;
        int currCost = 0;
        while(right < s.length()){
            currCost += Math.abs(s.charAt(right)-t.charAt(right));
            while(currCost > maxCost){
                currCost -= Math.abs(s.charAt(left)-t.charAt(left));
                left++;
            }
            maxLen = Math.max(maxLen, right-left+1);
            right++;
        }  
        return maxLen;
    }
}
```
