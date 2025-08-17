# Leetcode-2373.-Largest-Local-Values-in-a-Matrix
# Description
You are given an n x n integer matrix grid.

Generate an integer matrix maxLocal of size (n - 2) x (n - 2) such that:

maxLocal[i][j] is equal to the largest value of the 3 x 3 matrix in grid centered around row i + 1 and column j + 1.
In other words, we want to find the largest value in every contiguous 3 x 3 matrix in grid.

Return the generated matrix.
# Solution
You are given an n x n integer matrix grid.

Generate an (n - 2) x (n - 2) matrix res, where:res[i][j] = the maximum value of the 3 x 3 submatrix centered at grid[i+1][j+1]. Return res.
# Algorithm
1. Determine the size of the grid n.
2. Create a result matrix res of size (n-2) x (n-2) initialized with zeros.
3. For each position (i, j) in res:
4. Iterate over the 3x3 submatrix in grid starting at (i, j).
5. Find the maximum value inside that submatrix.
6. Store it in res[i][j].
7. Return the result matrix.
# Code
class Solution:

    def largestLocal(self, grid: List[List[int]]) -> List[List[int]]:
        n = len(grid)
        res = [([0] * (n - 2)) for _ in range(n - 2)]

        for i in range(n - 2):
            for j in range(n - 2):
                for r in range(i,i+ 3):
                    for c in range(j,j + 3):
                        res[i][j] = max(res[i][j], grid[r][c])

        return res
# Complexity
Time Complexity: 

O(n^2) → For each cell in (n-2) x (n-2), we check a fixed 3x3 block (constant work).

Space Complexity: 

O(n^2) → To store the result matrix.
