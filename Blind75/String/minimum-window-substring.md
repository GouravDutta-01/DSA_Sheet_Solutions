# [Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)
**Difficulty:** Hard

### Solution in Java
```java
class Solution {
    public String minWindow(String s, String t) {
        HashMap<Character, Integer> map = new HashMap<>();
        for(char ch : t.toCharArray()){
            map.put(ch, map.getOrDefault(ch, 0) + 1);
        }
        int left = 0;
        int right = 0;
        int count = 0;
        int minLen = Integer.MAX_VALUE;
        int startInd = -1;
        while(right < s.length()){
            char rChar = s.charAt(right);
            if(map.containsKey(rChar)){
                if(map.get(rChar) > 0){
                    count++;
                }
                map.put(rChar, map.get(rChar)-1);
            }
            while(count == t.length()){
                if(right-left+1 < minLen){
                    minLen = right-left+1;
                    startInd = left;
                }
                char lChar = s.charAt(left);
                if(map.containsKey(lChar)){
                    map.put(lChar, map.get(lChar)+1);
                    if(map.get(lChar) > 0){
                        count--;
                    }
                }
                left++;
            }
            right++;
        }
        return startInd != -1 ? s.substring(startInd, startInd+minLen) : "";  
    }
}
```
