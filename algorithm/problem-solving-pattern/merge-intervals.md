# Merge Intervals

## Description
The Merge Intervals technique is a common algorithmic approach used to merge overlapping intervals or ranges.
It is particularly useful when dealing with problems that involve intervals, such as scheduling, time management, or resource allocation.
The goal is to combine overlapping intervals into a consolidated set of non-overlapping intervals.

## Basic Explanation
1. Sort the intervals:
    - Begin by sorting the intervals based on their start points. This step ensures that overlapping intervals are adjacent to each other, making it easier to identify and merge them.

2. Initialize a result array:
    - Create an empty array to store the merged intervals.

3. Merge overlapping intervals:
    - Iterate through the sorted intervals, one by one, and compare each interval with the previous interval. If the current interval overlaps with the previous one, merge them into a single interval by updating the end point. If they don't overlap, add the previous interval to the result array and set the current interval as the new reference for comparison.

4. Add the last interval:
    - After the iteration, add the last interval (which may be the result of merging previous intervals) to the result array.

5. Return the merged intervals:
    - The result array now contains the merged intervals, which represent the non-overlapping ranges.


## Usage
1. Overlapping interval consolidation: 
    - It efficiently combines overlapping intervals into a consolidated set of non-overlapping intervals, simplifying subsequent calculations or analyses.

2. Time complexity optimization:
    - Sorting the intervals initially allows for a more efficient merging process, as adjacent intervals are more likely to overlap. This reduces the time complexity compared to alternative approaches.

4. Resource allocation and scheduling: 
    - Merge Intervals is commonly used in applications that involve allocating resources or scheduling tasks within a given time frame. It helps in identifying available time slots or resolving conflicts by merging overlapping intervals.

5. Calendar management: 
    - The technique can be employed in calendar management systems to merge overlapping events or appointments, ensuring accurate scheduling and avoiding conflicts.

6. Range-based queries: 
    - Merge Intervals can be used to optimize range-based queries or operations by reducing the number of intervals to consider. For example, finding the minimum number of meeting rooms required to accommodate a set of scheduled meetings.

## Problems

- [Merge Intervals](https://leetcode.com/problems/merge-intervals/)
- [Insert Interval](https://leetcode.com/problems/insert-interval/)
- [Interval List Intersections](https://leetcode.com/problems/interval-list-intersections/)

## Problem Statement 

### Merge Intervals
Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals.
and return an array of the non-overlapping intervals that cover all the intervals in the input.

### Approach:

1. Sort the intervals:
    - Start by sorting the intervals based on their start points. This step ensures that overlapping intervals are adjacent to each other.

2. Initialize a result array: 
    - Create an empty array to store the merged intervals.

3. Merge overlapping intervals: 
    - Iterate through the sorted intervals, one by one, and compare each interval with the last merged interval in the result array. 
    - If the current interval overlaps with the last merged interval, update the end point of the merged interval to be the maximum of the current interval's end point and the merged interval's end point. 
    - If they don't overlap, add the current interval to the result array as a new merged interval.

4. Return the merged intervals: 
    - The result array now contains the merged intervals, which represent the non-overlapping intervals that cover all the intervals in the input.

### Example Code
```python
def merge(intervals: List[List[int]]) -> List[List[int]]:
    intervals.sort()
    output = [intervals.pop(0)]

    for start, end in intervals:
        if output[-1][1] >= start:
            output[-1][1] = end if end > output[-1][1] else output[-1][1]
        else:
            output.append([start, end])

    return output

```
