
### 1. Reverse a Linked List

![LL1](../assets/LL1.png)

- there's 2 approaches  :
> 1. Iterative  = **O(n) TC and O(1) SC**
> 2. Recursive = **O(n) TC and O(n) SC**

- main idea is to store next link in a temp variable and then update pointers
![LL1-soln](../assets/LL1-soln.png)

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        prev = None
        curr = head
        while curr:
            temp = curr.next
            curr.next = prev
            prev = curr
            curr = temp

        return prev
```

---

### 2. Merge Two Sorted Lists

![LL2](../assets/LL2.png)

- to avoid edge cases in Linked List problems always create a ***dummy node (empty node)*** and start adding to that
- keep pointers at start of `List1` and `List2` , now compare these both and add the smaller one to output LL and after addition move pointer and compare and repeat

> #### *Just change the links within the LL and no need for extra space* 

![LL2-soln](../assets/LL2-soln.png)


```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        d = ListNode()
        cur = d

        while list1 and list2:
            if list1.val < list2.val:
                cur.next = list1
                cur = list1
                list1 = list1.next
            else:
                cur.next = list2
                cur = list2
                list2 = list2.next
        
        cur.next = list1 if list1 else list2
        
        return d.next
```