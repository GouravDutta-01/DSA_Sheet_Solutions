# [Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int characterReplacement(String s, int k) {
        int left = 0;
        int right = 0;
        int maxLen = 0;
        HashMap<Character, Integer> map = new HashMap<>();
        int maxFreq = 0;
        while(right < s.length()){
            char rChar = s.charAt(right);
            map.put(rChar, map.getOrDefault(rChar, 0) + 1);
            maxFreq = Math.max(maxFreq, map.get(rChar));
            while((right-left+1)-maxFreq > k){
                char lChar = s.charAt(left);
                map.put(lChar, map.get(lChar)-1);
                if(map.get(lChar) == 0){
                    map.remove(lChar);
                }
                left++;
            }
            maxLen = Math.max(maxLen, right-left+1);
            right++;
        }
        return maxLen;
    }
}
```
