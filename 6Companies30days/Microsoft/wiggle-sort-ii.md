# [Wiggle Sort II](https://leetcode.com/problems/wiggle-sort-ii/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public void wiggleSort(int[] nums) {
        ArrayList<Integer> list = new ArrayList<>();
        for(int val : nums){
            list.add(val);
        }
        Collections.sort(list);
        int ind = list.size()-1;
        for(int i=1; i<nums.length; i+=2){
            nums[i] = list.get(ind--);
        }
        for(int i=0; i<nums.length; i+=2){
            nums[i] = list.get(ind--);
        }
    }
}
```
