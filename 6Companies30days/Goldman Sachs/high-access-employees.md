# [High-Access Employees](https://leetcode.com/problems/high-access-employees/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public List<String> findHighAccessEmployees(List<List<String>> access_times) {
        HashMap<String, ArrayList<Integer>> map = new HashMap<>();
        for(List<String> list : access_times){
            String emp = list.get(0);
            int time = Integer.parseInt(list.get(1));
            if(!map.containsKey(emp)){
                map.put(emp, new ArrayList<>());
                map.get(emp).add(time);
            }
            else{
                map.get(emp).add(time);
            }
        }
        List<String> ans = new ArrayList<>();
        for(Map.Entry<String, ArrayList<Integer>> entry : map.entrySet()){
            String emp = entry.getKey();
            ArrayList<Integer> timeList = entry.getValue();
            Collections.sort(timeList);
            int left = 0;
            for(int right=0; right<timeList.size(); right++){
                while(timeList.get(right) - timeList.get(left) >= 100){
                    left++;
                }
                if(right-left+1 >= 3){
                    ans.add(emp);
                    break;
                }
            }
        }
        return ans;
    }
}
```
