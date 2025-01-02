# [Maximum Product of the Length of Two Palindromic Subsequences](https://leetcode.com/problems/maximum-product-of-the-length-of-two-palindromic-subsequences/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int maxProduct(String s) {
        return solve(0, s, "", "");
    }
    public int solve(int ind, String s, String s1, String s2){
        if(ind == s.length()){
            if(isPalindrome(s1) && isPalindrome(s2)){
                return s1.length()*s2.length();
            }
            return 0;
        }
        int take1 = solve(ind+1, s, s1 + s.charAt(ind), s2);
        int take2 = solve(ind+1, s, s1, s2 + s.charAt(ind));
        int notTake = solve(ind+1, s, s1, s2);
        return Math.max(take1, Math.max(take2, notTake));
    }
    public boolean isPalindrome(String s){
        int i = 0;
        int j = s.length()-1;
        while(i < j){
            if(s.charAt(i) != s.charAt(j)){
                return false;
            }
            i++;
            j--;
        }
        return true;
    }
}
```
