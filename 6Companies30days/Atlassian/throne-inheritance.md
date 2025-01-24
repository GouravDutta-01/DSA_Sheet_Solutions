# [Throne Inheritance](https://leetcode.com/problems/throne-inheritance/)
**Difficulty:** Medium

### Solution in Java
```java
class ThroneInheritance {
    String currKing;
    HashMap<String, List<String>> map;//parent-child map
    HashSet<String> finished;

    public ThroneInheritance(String kingName) {
        currKing = kingName;
        map = new HashMap<>();
        finished = new HashSet<>();
    }
    
    public void birth(String parentName, String childName) {
        if(map.containsKey(parentName)){
            map.get(parentName).add(childName);
        }
        else{
            map.put(parentName, new ArrayList<>());
            map.get(parentName).add(childName);
        }    
    }
    
    public void death(String name) {
        if(name == currKing){
            List<String> currInheritance = getInheritanceOrder();
            if(currInheritance.size() > 1){
                currKing = currInheritance.get(1);
            }
            else{
                currKing = "null";
            }
        }
        finished.add(name);
    }
    
    public List<String> getInheritanceOrder() {
        List<String> order = new ArrayList<>();
        successor(currKing, order);
        return order;
    }

    public void successor(String node, List<String> order){
        if(!finished.contains(node)){
            order.add(node);
        }
        if(!map.containsKey(node)){
            return;
        }
        for(String child : map.get(node)){
            successor(child, order);
        }
    }
}

/**
 * Your ThroneInheritance object will be instantiated and called as such:
 * ThroneInheritance obj = new ThroneInheritance(kingName);
 * obj.birth(parentName,childName);
 * obj.death(name);
 * List<String> param_3 = obj.getInheritanceOrder();
 */
```
