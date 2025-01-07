# [Delete N nodes after M nodes of a linked list](https://www.geeksforgeeks.org/problems/delete-n-nodes-after-m-nodes-of-a-linked-list/1)
**Difficulty:** Easy

### Solution in Java
```java
/*
delete n nodes after m nodes
The input list will have at least one element
Node is defined as
  class Node
  {
      int data;
      Node next;
      Node(int data)
      {
          this.data = data;
          this.next = null;
      }
  }
*/

class Solution {
    static void linkdelete(Node head, int n, int m) {
        Node curr = head;
        while(curr != null){
            int count = m-1;
            while(count-- > 0 && curr != null){
                curr = curr.next;
            }
            if(curr == null){
                break;
            }
            Node temp = curr;
            count = n+1;
            while(count-- > 0 && temp != null){
                temp = temp.next;
            }
            curr.next = temp;
            curr = curr.next;
        }
    }
}
```
