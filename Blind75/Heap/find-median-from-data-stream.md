# [Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/)
**Difficulty:** Hard

### Solution in Java
```java
class MedianFinder {
    PriorityQueue<Integer> s;//contains smaller half(max heap)
    PriorityQueue<Integer> g;//contains greater half(min heap)

    public MedianFinder() {
        s = new PriorityQueue<>(Collections.reverseOrder());
        g = new PriorityQueue<>();    
    }
    
    public void addNum(int num) {
        if(s.size() == 0){//first element
            s.add(num);
            return;
        }
        if(s.size() == g.size()){//add 1 more element in s
            if(num > g.peek()){
                s.add(g.poll());
                g.add(num);
            }
            else{
                s.add(num);
            }
        }
        else if(s.size() > g.size()){//add 1 more element in g
            if(num < s.peek()){
                g.add(s.poll());
                s.add(num);
            }
            else{
                g.add(num);
            }
        }    
    }
    
    public double findMedian() {
        if(s.size() != g.size()){//odd elements in current stream
            return s.peek();
        }
        else{
            return (double)(s.peek()+g.peek())/2;
        }   
    }
}

/**
 * Your MedianFinder object will be instantiated and called as such:
 * MedianFinder obj = new MedianFinder();
 * obj.addNum(num);
 * double param_2 = obj.findMedian();
 */
```
