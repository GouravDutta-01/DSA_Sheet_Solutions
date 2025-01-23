# [Friends Of Appropriate Ages](https://leetcode.com/problems/friends-of-appropriate-ages/)
**Difficulty:** Medium

### Solution in Java
```java
class Solution {
    public int numFriendRequests(int[] ages) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for(int age : ages){
            map.put(age, map.getOrDefault(age, 0) + 1);
        }
        int count = 0;
        for(Map.Entry<Integer, Integer> ageX : map.entrySet()){
            for(Map.Entry<Integer, Integer> ageY : map.entrySet()){
                if(isValid(ageX.getKey(), ageY.getKey())){
                    count += ageX.getValue()*ageY.getValue();
                    if(ageX == ageY){//remove combination of requests between same person
                        count -= ageX.getValue();
                    }
                }
            }
        }
        return count;
    }
    public boolean isValid(int ageX, int ageY){
        return (!(ageY <= 0.5*ageX+7 || ageY > ageX || (ageY > 100 && ageX < 100)));
    }
}
```
