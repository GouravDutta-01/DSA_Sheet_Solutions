# [K Divisible Elements Subarrays](https://leetcode.com/problems/k-divisible-elements-subarrays/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int countDistinct(int[] nums, int k, int p) {
        int ans = 0;
        int n = nums.length;
        HashSet<String> set = new HashSet<>();
        for(int i=0; i<n; i++){
            StringBuilder sb = new StringBuilder();
            int count = 0;
            for(int j=i; j<n; j++){
                sb.append(nums[j]).append("#");
                if(nums[j] % p == 0){
                    count++;
                }
                if(count > k){
                    break;
                }
                String str = sb.toString();
                if(!set.contains(str)){
                    set.add(str);
                    ans++;
                }
            }
        }
        return ans;
    }
}
```