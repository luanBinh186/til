# Two pointers

## Description
The Two Pointers pattern is a technique used in computer programming and algorithms to solve certain problems more efficiently. It involves using two pointers that traverse a data structure (like an array or linked list) in a way that helps optimize the algorithm's time or space complexity.

## Basic Explanation
1. Initialization: Initialize two pointers at different positions in the data structure.

2. Movement: Adjust the positions of the pointers based on certain conditions or criteria.

3. Termination: Continue moving the pointers until a certain condition is met, such as reaching the end of the array or satisfying a specific requirement.


## Usage
This pattern is often used in problems where you need to find a pair or a subarray with a certain property, or when you are required to optimize a solution that involves iterating over the elements of a data structure.

Example scenarios where the Two Pointers pattern is commonly applied include finding pairs in a sorted array, searching for a target sum in a sorted array, or detecting a cycle in a linked list.

Using the Two Pointers pattern can lead to more efficient solutions compared to brute force approaches in certain cases, as it takes advantage of the inherent structure or properties of the data.

## Problems
[Two Sum](https://leetcode.com/problems/two-sum/), [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/), [Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/)


## Problem Statement 
### Pair with Target Sum
Given a sorted array of integers and a target sum, find a pair of elements in the array whose sum is equal to the target.

### Algorithm using Two Pointers:

1. Initialize two pointers, ```left``` at the beginning of the array and ```right``` at the end.
2. While **left** is less than ```right```, do the following:
    - Calculate the sum of elements at positions ```left``` and ```right```.
    - If the sum equals the target, you've found the pair.
    - If the sum is less than the target, move the ```left``` pointer to the ```right```.
    - If the sum is greater than the target, move the ```right``` pointer to the ```left```.
3. Repeat until the pointers meet or the pair is found.

### Example Code:
```python
def two_sum_sorted_array(nums, target):
    left, right = 0, len(nums) - 1

    while left < right:
        current_sum = nums[left] + nums[right]

        if current_sum == target:
            return [nums[left], nums[right]]
        elif current_sum < target:
            left += 1
        else:
            right -= 1

    return None  # No such pair found


sorted_array = [-2, 1, 2, 4, 7, 11]
target_sum = 13
result = two_sum_sorted_array(sorted_array, target_sum)
print(result)  # Output: [2, 11]
```

