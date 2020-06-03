# 題目：[Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)

Reverse a singly linked list.

### **Example:**

```
Input: 1->2->3->4->5->NULL
Output: 5->4->3->2->1->NULL
```

---

## 解法

``` java
class Solution {

    ListNode tmp = null;
    ListNode result = null;

    public ListNode reverseList(ListNode head) {
        if (head == null) {
            return null;
        }
        ListNode node = reverseList(head.next);
        if (node == null) {
            result = tmp = head;
        } else {
            tmp.next = head;
            tmp = tmp.next;
            tmp.next = null;
        }
        return result;
    }
}
```
