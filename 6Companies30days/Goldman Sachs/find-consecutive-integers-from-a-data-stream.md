# [Find Consecutive Integers from a Data Stream](https://leetcode.com/problems/find-consecutive-integers-from-a-data-stream/)
**Difficulty:** Medium

### Solution in Java
```java
class DataStream {
    int consecCount;
    int value;
    int k;

    public DataStream(int value, int k) {
        consecCount = 0;
        this.value = value;
        this.k = k;   
    }
    
    public boolean consec(int num) {
        if(num == value){
            consecCount++;
        }
        else{
            consecCount = 0;
        }
        return consecCount >= k;  
    }
}

/**
 * Your DataStream object will be instantiated and called as such:
 * DataStream obj = new DataStream(value, k);
 * boolean param_1 = obj.consec(num);
 */
```