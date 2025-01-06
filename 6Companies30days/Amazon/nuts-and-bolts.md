# [Nuts and Bolts](https://www.geeksforgeeks.org/problems/nuts-and-bolts-problem0431/1)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    void matchPairs(int n, char nuts[], char bolts[]) {
        char[] dict = new char[]{'!', '#', '$', '%', '&', '*', '?', '@', '^'};
        HashSet<Character> set = new HashSet<>();
        for(int i=0; i<nuts.length; i++){
            set.add(nuts[i]);
        }
        int ind = 0;
        for(char ch : dict){
            if(set.contains(ch)){
                nuts[ind] = ch;
                bolts[ind] = ch;
                ind++;
            }
        }
    }
}
```
