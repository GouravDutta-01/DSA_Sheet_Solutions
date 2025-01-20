# [Combination Sum III](https://leetcode.com/problems/combination-sum-iii/)
**Difficulty:** Medium

### Solution 1 in Java
```java
class Solution {
    public List<List<Integer>> combinationSum3(int k, int n) {
        List<List<Integer>> ans = new ArrayList<>();
        solve(1, k, n, new ArrayList<>(), ans);
        return ans;   
    }
    public void solve(int i, int k, int n, List<Integer> curr, List<List<Integer>> ans){
        if(k == 0 && n == 0){
            ans.add(new ArrayList<>(curr));
            return;
        }
        if(k == 0 || n == 0 || i == 10){
            return;
        }
        if(i <= n){
            curr.add(i);
            solve(i+1, k-1, n-i, curr, ans);
            curr.remove(curr.size()-1);
        }
        solve(i+1, k, n, curr, ans);
    }
}
```
### Solution 2 in Java
```java
class Solution {
    public List<List<Integer>> combinationSum3(int k, int n) {
        List<List<Integer>> ans = new ArrayList<>();
        solve(1, k, n, new ArrayList<>(), ans);
        return ans;   
    }
    public void solve(int start, int k, int n, List<Integer> curr, List<List<Integer>> ans){
        if(k == 0 && n == 0){
            ans.add(new ArrayList<>(curr));
            return;
        }
        if(k == 0 || n == 0){
            return;
        }
        for(int i=start; i<=9; i++){
            if(i <= n){
                curr.add(i);
                solve(i+1, k-1, n-i, curr, ans);
                curr.remove(curr.size()-1);
            }
        }
    }
}
```