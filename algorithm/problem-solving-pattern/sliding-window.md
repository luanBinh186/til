# Sliding window

## Description
Sliding window technique, also known as the sliding window algorithm or sliding window protocol, is a common approach used in computer science and data processing to efficiently process or analyze a sequence of data elements.
It involves dividing the data into fixed-size segments or "windows" and performing operations on each window as it slides through the larger data set.

## Basic Explanation
The basic idea behind the sliding window technique is to avoid redundant computations by reusing intermediate results. 
Instead of processing the entire data set repeatedly, the algorithm processes only the elements within the current window and updates the results based on the incoming and outgoing elements as the window slides forward.

## Usage
1. Define the window size:
    - Determine the fixed size of the window that will be used to process the data. The window size can vary depending on the problem or application.

2. Initialize the window: 
    - Start by processing the first window of data elements, which includes the first 'n' elements from the data set, where 'n' is the window size.

3. Process the window: 
    - Perform the desired operations or computations on the elements within the window. This could involve calculating sums, averages, finding maximum or minimum values, searching for patterns, or any other relevant processing task.

4. Slide the window: 
    - Slide the window by moving one element at a time, either to the right or left, depending on the specific problem. As the window slides, update the results based on the new incoming element and the outgoing element that falls outside the window.

5. Repeat until the end: 
    - Continue sliding the window through the entire data set until all elements have been processed. This ensures that every element is considered in at least one window.

## Problems
1. Data stream analytics: 
    - Analyzing real-time data streams, such as sensor data, network traffic, or financial market data, to detect trends, anomalies, or patterns.

2. Image processing: 
    - Applying filters or transformations to images by considering a fixed-size window of pixels at a time.

3. Natural language processing: 
    - Analyzing text data, such as sentiment analysis or named entity recognition, by sliding a window over the text to extract relevant features or information.

4. Genetic sequence analysis:
    - Identifying patterns or motifs in DNA or protein sequences by sliding a window over the sequence data.

## Problems
- [Maximum Sum of Distinct Subarrays With Length K](https://leetcode.com/problems/maximum-sum-of-distinct-subarrays-with-length-k/)
- [Fruit Into Baskets](https://leetcode.com/problems/fruit-into-baskets/)

## Problem Statement 

### Fruit Into Baskets

You are visiting a farm that has a single row of fruit trees arranged from left to right. The trees are represented by an integer array fruits where fruits[i] is the type of fruit the ith tree produces.

### Approach:

- The window expands to the right (r increases) and contracts to meet the constraint (l increases) when there are more than two types of fruits in the window.
- By keeping track of the fruit frequencies using the cnt counter and updating the window accordingly, the code efficiently finds the maximum number of fruits that can be picked.

```python
def totalFruit(self, fruits: List[int]) -> int:
    k = 0
    l = 0
    seen = {}
    for i in range(len(fruits)):
        seen[fruits[i]] = seen.get(fruits[i], 0) + 1
        if len(seen) <= 2:
            k = max(k, i - l + 1)
        else:
            seen[fruits[l]] -= 1
            if seen[fruits[l]] == 0:
                seen.pop(fruits[l])
            l += 1
    return k
```
