# leet-day29

# Unique Paths

You are given an `m x n` grid representing a rectangular grid. The task is to find the number of possible unique paths for a robot located at the top-left corner to reach the bottom-right corner. The robot can only move either down or right at any point in time.

The goal is to determine the total number of unique paths the robot can take to reach its destination.

## Example

**Input:**
```
m = 3, n = 7
```

**Output:**
```
28
```

**Explanation:**
From the top-left corner, there are a total of 28 unique ways to reach the bottom-right corner:
1. Right -> Right -> Right -> Right -> Down -> Down -> Down
2. Right -> Right -> Right -> Down -> Down -> Right -> Down
3. Right -> Right -> Down -> Down -> Right -> Right -> Down
...
28. Down -> Down -> Down -> Right -> Right -> Right -> Right

## Approach

We can use dynamic programming to solve this problem. The basic idea is to maintain a 2D array `dp`, where `dp[i][j]` represents the number of unique paths to reach cell `(i, j)`.

1. Initialize the leftmost column and top row of the `dp` array to 1, as there is only one way to reach any cell in these rows/columns (either moving right or down).
2. For each cell `(i, j)` in the grid, calculate `dp[i][j]` using the recurrence relation: `dp[i][j] = dp[i-1][j] + dp[i][j-1]`. This is because the robot can only move either down from the cell above or right from the cell on the left.

Finally, the value of `dp[m - 1][n - 1]` will represent the number of unique paths from the top-left corner to the bottom-right corner of the grid.

## Complexity Analysis

The time complexity of this solution is O(m * n), where `m` is the number of rows and `n` is the number of columns in the grid. The space complexity is also O(m * n) as we are using a 2D array to store the intermediate results.
