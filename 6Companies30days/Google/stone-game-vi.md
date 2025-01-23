# [Stone Game VI](https://leetcode.com/problems/stone-game-vi/)
**Difficulty:** Medium

### Solution in Java
```java
class Pair{
    int val;
    int ind;
    public Pair(int val, int ind){
        this.val = val;
        this.ind = ind;
    }
}
class Solution {
    public int stoneGameVI(int[] aliceValues, int[] bobValues) {
        PriorityQueue<Pair> pq = new PriorityQueue<>((a, b) -> b.val - a.val);
        for(int i=0; i<aliceValues.length; i++){
            pq.add(new Pair(aliceValues[i]+bobValues[i], i));
        }
        boolean alice = true;
        int countAlice = 0;
        int countBob = 0;
        while(!pq.isEmpty()){
            Pair curr = pq.poll();
            if(alice){
                countAlice += aliceValues[curr.ind];
            }
            else{
                countBob += bobValues[curr.ind];
            }
            alice = !alice;  
        }
        if(countAlice > countBob){
            return 1;
        }
        else if(countAlice < countBob){
            return -1;
        }
        else{
            return 0;
        }
    }
}
```
### Note:
- Here we sort by sum of values of alice and bob on each indices because for alice to play optimally it wants to take index where maximum of her value is present or maximum of bob's value is present and vice versa

