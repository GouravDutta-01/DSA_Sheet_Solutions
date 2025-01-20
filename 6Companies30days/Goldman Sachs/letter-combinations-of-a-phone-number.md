# [Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public List<String> letterCombinations(String digits) {
        if(digits.equals("")){
            return new ArrayList<>();
        }
        HashMap<Integer, String> map = new HashMap<>();
        map.put(2, "abc");
        map.put(3, "def");
        map.put(4, "ghi");
        map.put(5, "jkl");
        map.put(6, "mno");
        map.put(7, "pqrs");
        map.put(8, "tuv");
        map.put(9, "wxyz");
        List<String> ans = new ArrayList<>();
        solve(0, digits, new StringBuilder(), ans, map);
        return ans;
    }
    public void solve(int ind, String digits, StringBuilder curr, List<String> ans, HashMap<Integer, String> map){
        if(ind == digits.length()){
            ans.add(curr.toString());
            return;
        }
        int digit = digits.charAt(ind)-'0';
        String str = map.get(digit);
        for(char ch : str.toCharArray()){
            curr.append(ch);
            solve(ind+1, digits, curr, ans, map);
            curr.deleteCharAt(curr.length()-1);
        }
    }
}
```