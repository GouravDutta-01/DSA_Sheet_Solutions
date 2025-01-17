# [Assign Cookies](https://leetcode.com/problems/assign-cookies/)
**Difficulty:** Easy

### Solution in Java
```java
class Solution {
    public int findContentChildren(int[] g, int[] s) {
        Arrays.sort(g);
        Arrays.sort(s);
        int i = 0;
        int j = 0;
        int count = 0;
        while(j < s.length && i < g.length){
            if(g[i] <= s[j]){//Greedily assigning smallest possible cookies to the students who have least greed first
                count++;
                i++;
                j++;
            }
            else{
                j++;
            }
        }
        return count;
    }
}
```