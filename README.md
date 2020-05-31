# Maximal Square
## https://leetcode.com/problems/maximal-square

# Implementation 1 :

```java
class Solution {
    public int maximalSquare(char[][] matrix) {
        if(matrix == null || matrix.length == 0)
            return 0;
        int maxSquareSize = 0;
        int rows = matrix.length;
        int cols = matrix[0].length;
        
        int[][] dp = new int[rows + 1][cols + 1];
        for(int row = 1; row <= rows; row++) {
            for(int col = 1; col <= cols; col++) {
                if(matrix[row - 1][col - 1] == '1') {
                    int min = Math.min(dp[row][col - 1], dp[row - 1][col]);
                    min = Math.min(min, dp[row - 1][col - 1]);
                    dp[row][col] = min + 1;
                    
                    maxSquareSize = Math.max(maxSquareSize, dp[row][col]);
                }
            }
        }
       return maxSquareSize * maxSquareSize; 
    }
}
```


# References :
https://leetcode.com/articles/maximal-square
