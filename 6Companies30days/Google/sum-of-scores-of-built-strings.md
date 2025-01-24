# [Sum of Scores of Built Strings](https://leetcode.com/problems/sum-of-scores-of-built-strings/)
**Difficulty:** Hard

### Solution in Java
```java
class Solution {
    public long sumScores(String s) {
        int n = s.length();
        int[] z = new int[n];//z[i] represents greatest no. of characters starting from i that are equal to the first characters of s
        int l = 0;
        int r = 0;
        for(int i=1; i<n; i++){
            if(i > r){//out of window
                while(i + z[i] < n && s.charAt(i + z[i]) == s.charAt(z[i])){
                    z[i]++;
                }
                l = i;
                r = i + z[i] - 1;
            }
            else{//within window boundary
                if(i + z[i-l] <= r){//within window boundary
                    z[i] = z[i-l];
                }
                else{//take z[i] value till window boundary and then match more after boundary
                    z[i] = r-i+1;
                    while(i + z[i] < n && s.charAt(i + z[i]) == s.charAt(z[i])){
                        z[i]++;
                    }
                    l = i;
                    r = i + z[i] - 1;
                }
            }
        }
        long scoreSum = 0;
        for(int val : z){
            scoreSum += val;
        }
        return scoreSum + n;    
    }
}
```
