# [Run Length Encoding](https://www.geeksforgeeks.org/problems/run-length-encoding/1)
**Difficulty:** Easy

### Solution in Java
```java
class Solution {
    public static String encode(String s) {
        int currFreq = 1;
        StringBuilder sb = new StringBuilder();
        for(int i=1; i<s.length(); i++){
            if(s.charAt(i) == s.charAt(i-1)){
                currFreq++;
            }
            else{
                sb.append(s.charAt(i-1)).append(currFreq);
                currFreq = 1;
            }
        }
        sb.append(s.charAt(s.length()-1)).append(currFreq);
        return sb.toString();
    }
}
```