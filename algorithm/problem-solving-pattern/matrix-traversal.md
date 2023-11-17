# Matrix Traversa

## Description
The "Island Matrix Traversal" technique is used to identify and count connected components, often referred to as "islands," in a 2D matrix. In this context, an island is a group of adjacent elements in the matrix that share the same value (e.g., 1 for land). 
The technique employs Depth-First Search (DFS) or Breadth-First Search (BFS) to traverse through the matrix and identify these connected components.

## Basic Explanation
1. Traversal:
    - The algorithm iterates through each cell in the matrix.
    - When a cell with a specific property (e.g., value 1) is encountered, a traversal is initiated to explore and mark all connected cells.

2. DFS or BFS:
    - Depth-First Search (DFS) is commonly used for this problem. It involves exploring as far as possible along each branch before backtracking.
    - Breadth-First Search (BFS) is an alternative. It explores all the neighbors at the present depth prior to moving on to nodes at the next depth level.

3. Marking Cells:
    - To avoid redundant counting of the same island, cells within an identified island are typically marked or modified.
    - This prevents revisiting the same cells during subsequent traversals.

## Usage

* Graph Algorithms:
    * Island Matrix Traversal is commonly used in graph algorithms to analyze and understand the connectivity of components in a matrix.

* Image Processing:
    * In image processing, this technique can be applied to identify and analyze regions or objects within an image.

* Game Development:
    * In game development, especially for grid-based games, this technique can be used to detect and manage regions such as territories or connected areas.

* Network Analysis:
    * It can be adapted for network analysis to find connected components in networks represented as adjacency matrices.

* Puzzle Solving:
    * Island Matrix Traversal is useful for solving puzzles that involve identifying and counting connected components.
## Problems
- [Number of Islands](https://leetcode.com/problems/number-of-islands/)
- [Max Area of Island](https://leetcode.com/problems/max-area-of-island/)
- [Flood Fill](https://leetcode.com/problems/flood-fill/)

## Problem Statement 

### Number of Islands
Given a 2D matrix of 0s and 1s, where 0 represents water and 1 represents land, determine the number of islands. 
An island is a group of connected 1s (either horizontally or vertically). Diagonal connections are not considered.

### Approach:
1. Iterative DFS (Depth-First Search)
    - Iterate through each cell in the matrix.
    - If the cell contains a 1 (land), perform a DFS to mark all connected land cells.
    - Increment the count of islands for each DFS traversal.

2. Marking Cells
    - To avoid counting the same island multiple times, mark the visited cells (set them to 0 or some other marker).

### Example Code:

```python
def numIslands(grid):
    if not grid or not grid[0]:
        return 0

    def dfs(i, j):
        if 0 <= i < len(grid) and 0 <= j < len(grid[0]) and grid[i][j] == 1:
            grid[i][j] = 0  # Mark the cell as visited
            # Explore all four directions
            dfs(i + 1, j)
            dfs(i - 1, j)
            dfs(i, j + 1)
            dfs(i, j - 1)

    island_count = 0
    for i in range(len(grid)):
        for j in range(len(grid[0])):
            if grid[i][j] == 1:
                island_count += 1
                dfs(i, j)

    return island_count

matrix = [
    [1, 1, 0, 0, 0],
    [1, 1, 0, 0, 0],
    [0, 0, 1, 0, 0],
    [0, 0, 0, 1, 1]
]

result = numIslands(matrix)
print(result)  # Output: 3

```
