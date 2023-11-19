# Fast & Slow Pointers

## Description
The "Fast & Slow Pointers" pattern is a popular technique used in solving problems related to linked lists and arrays. It involves using two pointers that traverse the data structure at different speeds (hence the name "Fast & Slow") to identify a specific condition or solve a problem. 
This pattern is particularly useful for detecting cycles, finding midpoints, and solving related problems efficiently.

## Basic Explanation
1. Two Pointers:
    - Initialize two pointers, often called "fast" and "slow," both initially pointing to the head (start) of the linked list or array.
2. Movement:
    - Move the "fast" pointer at a faster rate than the "slow" pointer. The speed of movement depends on the specific problem.
3. Condition Check:
    - Use the movement of these pointers to identify a specific condition, such as meeting at a common point (cycle detection), reaching the end of the list, or finding a specific value.
4. Cycle Detection:
    - In the context of linked lists, if there is a cycle, the fast and slow pointers will eventually meet at some point within the cycle.

## Usage
1. Cycle Detection in Linked Lists:
    - Fast & Slow Pointers can be used to detect cycles in a linked list. If there is a cycle, the fast pointer will eventually catch up with the slow pointer within the cycle.
2. Finding the Middle of a Linked List:
    - By moving the fast pointer twice as fast as the slow pointer, when the fast pointer reaches the end, the slow pointer will be at the middle of the linked list.
3. Two Pointers in Arrays:
    - The pattern can be applied to arrays for problems like finding pairs that satisfy certain conditions or identifying a specific value.


## Problems

- [LinkedList Cycle](https://leetcode.com/problems/linked-list-cycle/)
- [Middle of the LinkedList](https://leetcode.com/problems/middle-of-the-linked-list/)
- [Palindrome LinkedList](https://leetcode.com/problems/palindrome-linked-list/)


## Problem Statement 

### Palindrome LinkedList

Given the head of a singly linked list, return true if it is a palindrome or false otherwise.

### Approach:

1. Find the Middle:
    - Use the Fast & Slow Pointers technique to find the middle of the linked list.
2. Reverse the Second Half:
    - Reverse the second half of the linked list.
3. Compare the Reversed Second Half with the First Half:
    - Compare the reversed second half of the linked list with the first half to check if they are the same.


### Example Code

```python
class ListNode:
    def __init__(self, value):
        self.value = value
        self.next = None

def is_palindrome(head):
    # Find the middle using Fast & Slow Pointers
    slow = head
    fast = head
    while fast is not None and fast.next is not None:
        slow = slow.next
        fast = fast.next.next

    # Reverse the second half of the linked list
    second_half = reverse_linked_list(slow)

    # Compare the reversed second half with the first half
    while second_half is not None:
        if head.value != second_half.value:
            return False
        head = head.next
        second_half = second_half.next
    return True

def reverse_linked_list(head):
    prev = None
    current = head

    while current is not None:
        next_node = current.next
        current.next = prev
        prev = current
        current = next_node

    return prev
```