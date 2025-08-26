## Sum Of all elements of a Matrix
- First apply prefix sum on each row.
- Apply Prefix sum on all the columns.
- The bottom right element is the sum of all elements of the matrix.

## Sum of all elements of a submatrix (One end of the diagonal is at the origin)
- Assuming you already have prefix sum of the entire matrix, the sum will be the other end of the submatrix diagonal.

## Sum of all elements of a submatrix (neither ends of diagonal are at origin)
- Assume submatrix has coordinates (r1, c1) and (r2, c2) representing the ends of the diagonal.
- Get prifix sum value at the bottom right corner (r2, c2) of the submatrix. call it full.
- Get prefix sum of the matrix left of the submatrix (r2, c1-1). Call it left.
- Get prefix sum of the matrix above of the submatrix (r1-1, c2). Call it top.
- Get prifix sum value at the top left corner (r1-1, c2-1) of the submatrix. call it topleft.
- Submatrix sum is (full + topleft) - top - left.

### Code
```class PrefixSumMat():
    def __init__(self, mat):
        ROWS= len(mat)
        COLS= len(mat[0])
        
        for row in range(0, ROWS):
            for col in range(1, COLS):
                mat[row][col]= mat[row][col-1] + mat[row][col]
        
        for col in range(0, COLS):
            for row in range(1, ROWS):
                mat[row][col]= mat[row-1][col] + mat[row][col]
                
    def get_matrix_sum(self, mat, row, col):
        return mat[row][col]
        
    def get_submatrix_sum(self, mat, r1, c1, r2, c2):
        ROWS= len(mat)
        COLS= len(mat[0])
        if r1 > ROWS or r1 > ROWS or c1 > COLS or c2 > COLS: return 0
        
        full= self.get_matrix_sum(mat, r2, c2)
        left= 0
        if c1 > 0:
            left= self.get_matrix_sum(mat, r2, c1-1)
        
        top= 0
        if r1 > 0:
            top= self.get_matrix_sum(mat, r1-1, c2)
        
        topleft= 0    
        if r1 > 0 and c1 > 0:
            topleft= self.get_matrix_sum(mat, r1-1, c1-1)
        
        return (full + topleft) - top - left
```


