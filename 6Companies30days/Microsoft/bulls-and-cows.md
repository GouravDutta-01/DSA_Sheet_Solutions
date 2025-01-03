# [Bulls and Cows](https://leetcode.com/problems/bulls-and-cows/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public String getHint(String secret, String guess) {
        int n = guess.length();
        int bulls = 0;
        int cows = 0;
        int[] s = new int[10];
        int[] g = new int[10];
        for(int i=0; i<n; i++){
            if(secret.charAt(i) == guess.charAt(i)){
                bulls++;
            }
            else{
                s[secret.charAt(i)-'0']++;
                g[guess.charAt(i)-'0']++;
            }
        }
        for(int i=0; i<10; i++){
            cows += Math.min(g[i], s[i]);
        }
        StringBuilder sb = new StringBuilder();
        sb.append(bulls + "A" + cows + "B");
        return sb.toString();    
    }
}
```
