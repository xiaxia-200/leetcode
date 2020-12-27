## 566 重塑矩阵
### 解题思路
* 首先判断重塑是否合理，如果新矩阵的元素个数与原来的不相等，则不进行任何操作，直接输出原矩阵
* 重塑操作合理时，按行优先遍历的顺序扫描原二维数组，同时将元素按照行优先的顺序，依次放入到新二维数组中
### 代码
```java
class Solution {
    public int[][] matrixReshape(int[][] nums, int r, int c) {
        int sum = nums.length * nums[0].length;
        if(sum != r * c)//reshape操作不合理时输出原矩阵
            return nums;

        int[][] result = new int[r][c];
        int i = 0, j = 0;

        for(int nums1[] : nums){//按行遍历nums
            for(int num : nums1){
                result[i][j++] = num;//将元素顺序放入新矩阵
                if(j >= c){
                    j = 0;
                    i++;
                }                   
                if(i >= r)
                    break;
            }           
        }
        return result;
    }
}
```
### 复杂度分析
时间复杂度O(m*n)，空间复杂度O(m*n);m n分别是nums的行数和列数