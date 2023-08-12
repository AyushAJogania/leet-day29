# leet-day29

# Unique Paths II with Obstacles

## Problem Description

You are given a grid with obstacles, where each cell can either be empty or blocked by an obstacle. The goal is to find the number of unique paths a robot can take from the top-left corner to the bottom-right corner of the grid. The robot can only move right or down and cannot pass through obstacles.

## Approach

The problem can be efficiently solved using dynamic programming. We will create a 2D array `dp` where `dp[i][j]` represents the number of unique paths to reach cell `(i, j)`. We will iterate through each cell in the grid, and if the cell is not an obstacle, we will update `dp[i][j]` by adding the number of unique paths from the cells above `(i-1, j)` and left `(i, j-1)`.

## Algorithm

1. Initialize a 2D array `dp` of size `m x n`, where `m` is the number of rows and `n` is the number of columns of the grid.

2. Set `dp[0][0]` to 1 if the top-left cell is not an obstacle.

3. Iterate through each cell in the grid using two nested loops:

   a. If the current cell is an obstacle, set `dp[i][j]` to 0.
   
   b. Otherwise, update `dp[i][j]` by adding `dp[i-1][j]` and `dp[i][j-1]`.

4. The value of `dp[m-1][n-1]` will represent the number of unique paths from the top-left to the bottom-right cell of the grid.

5. Return `dp[m-1][n-1]` as the result.

## Complexity Analysis

- Time complexity: O(m * n), where `m` is the number of rows and `n` is the number of columns of the grid.
- Space complexity: O(m * n) to store the `dp` array.

## Implementation

```cpp
class Solution {
public:
    int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
        int m = obstacleGrid.size();
        int n = obstacleGrid[0].size();
        
        vector<vector<long long>> dp(m, vector<long long>(n, 0));
        
        dp[0][0] = (obstacleGrid[0][0] == 0) ? 1 : 0;
        
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (obstacleGrid[i][j] == 1) {
                    dp[i][j] = 0;
                } else {
                    if (i > 0) {
                        dp[i][j] += dp[i - 1][j];
                    }
                    if (j > 0) {
                        dp[i][j] += dp[i][j - 1];
                    }
                }
            }
        }
        
        return dp[m - 1][n - 1];
    }
};
```

This solution efficiently solves the problem of finding the number of unique paths in a grid with obstacles using dynamic programming.
