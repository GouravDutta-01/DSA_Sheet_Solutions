# [Combination Sum](https://leetcode.com/problems/combination-sum/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> ans = new ArrayList<>();
        solve(0, new ArrayList<>(), candidates, target, ans);
        return ans;
    }
    public void solve(int ind, ArrayList<Integer> curr, int[] candidates, int target, List<List<Integer>> ans){
        if(target == 0){
            ans.add(new ArrayList<>(curr));
            return;
        }
        if(ind == candidates.length){
            return;
        }
        if(target >= candidates[ind]){
            curr.add(candidates[ind]);
            solve(ind, curr, candidates, target-candidates[ind], ans);
            curr.remove(curr.size()-1);
        }
        solve(ind+1, curr, candidates, target, ans);
    }
}
``