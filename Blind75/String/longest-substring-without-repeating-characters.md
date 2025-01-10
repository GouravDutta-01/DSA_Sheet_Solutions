# [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
**Difficulty:** Medium

### Solution 1 in Java
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int maxLen = 0;
        HashMap<Character, Integer> map = new HashMap<>();
        int left = 0;
        int right = 0;
        while(right < s.length()){
            char rChar = s.charAt(right);
            map.put(rChar, map.getOrDefault(rChar, 0) + 1);
            while(map.size() != right-left+1){
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
### Solution 2 in Java
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int maxLen = 0;
        HashMap<Character, Integer> map = new HashMap<>();//{key, value} => {character, rightMost position of character}
        int left = 0;
        int right = 0;
        while(right < s.length()){
            char rChar = s.charAt(right);
            if(map.containsKey(rChar)){
                left = Math.max(left, map.get(rChar)+1);//take max of current left and previous right-most position of the current character
            }
            map.put(rChar, right);
            maxLen = Math.max(maxLen, right-left+1);
            right++;
        }
        return maxLen;
    }
}
```
