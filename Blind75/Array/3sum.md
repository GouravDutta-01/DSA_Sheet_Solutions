# [3Sum](https://leetcode.com/problems/3sum/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        int n = nums.length;
        HashSet<List<Integer>> set = new HashSet<>();
        for(int i=0; i<n; i++){
            HashMap<Integer, Integer> map = new HashMap<>();
            for(int j=i+1; j<n; j++){
                if(map.containsKey(-nums[j]-nums[i])){
                    int k = map.get(-nums[j]-nums[i]);
                    ArrayList<Integer> curr = new ArrayList<>(Arrays.asList(nums[i], nums[j], nums[k]));
                    Collections.sort(curr);
                    set.add(curr);
                }
                map.put(nums[j], j);
            }
        }
        return new ArrayList<>(set);  
    }
}
```
