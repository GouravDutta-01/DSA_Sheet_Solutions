# [LRU Cache](https://leetcode.com/problems/lru-cache/)
**Difficulty:** Medium

### Solution 1 in Java
```java
class LRUCache {
    LinkedHashMap<Integer, Integer> map;
    int capacity;

    public LRUCache(int capacity) {
        map = new LinkedHashMap<>();
        this.capacity = capacity;
    }
    
    public int get(int key) {
        if(map.containsKey(key)){
            int val = map.get(key);
            map.remove(key);
            map.put(key, val);
            return val;
        }
        return -1;
    }
    
    public void put(int key, int value) {
        if(map.containsKey(key)){
            map.remove(key);
            map.put(key, value);
            return;
        }
        if(map.size() == capacity){
            int lruKey = -1;
            for(Map.Entry<Integer, Integer> entry : map.entrySet()){
                lruKey = entry.getKey();
                break;
            }
            map.remove(lruKey);
        }
        map.put(key, value);
    }
}

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache obj = new LRUCache(capacity);
 * int param_1 = obj.get(key);
 * obj.put(key,value);
 */
```
