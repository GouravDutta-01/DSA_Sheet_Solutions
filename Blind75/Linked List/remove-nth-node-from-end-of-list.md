# [Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)
**Difficulty:** Medium

### Solution in Java
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        int size = 0;
        ListNode temp = head;
        while(temp != null){
            temp = temp.next;
            size++;
        }
        if(size == n){
            return head.next;
        }
        temp = head;
        int k = size-n+1;//nth node from end is kth node from start
        while(k-- > 2){//stop temp one node before the kth node
            temp = temp.next;
        }
        temp.next = temp.next.next;
        return head;   
    }
}
```
