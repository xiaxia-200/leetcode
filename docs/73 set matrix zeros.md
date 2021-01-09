## 73 矩阵置零
### 解题思路
使用两个额外的数据记录需要变动的行和列，在最后一次扫描过程中根据行列值，将对应的行和列的元素都置为零
### 代码
```java
class Solution {
    public void setZeroes(int[][] matrix) {

        int[] row = new int[matrix.length];
        int[] line = new int[matrix[0].length];

        //将标记数组赋予初值，如果数组元素不等于0则说明这一行/列不需要改动
        for(int i = 0; i < matrix.length; i++)
            row[i] = matrix.length;
        for(int j = 0; j < matrix[0].length; j++)
            line[j] = matrix[0].length;         

        //判断这一行/列是否需要置0
        for(int i = 0; i < matrix.length; i++){
            for(int j = 0; j < matrix[0].length; j++){
                if(matrix[i][j] == 0){
                    row[i] = 0;
                    line[j] = 0;
                }
            }
        }

        //根据标记改变元素
        for(int i = 0; i < matrix.length; i++){
            if(row[i] == 0){
                for(int j = 0; j < matrix[0].length; j++)
                    matrix[i][j] = 0;
            }
        }
        for(int j = 0; j < matrix[0].length; j++){
            if(line[j] == 0){
                for(int i = 0; i < matrix.length; i++)
                    matrix[i][j] = 0;
            }
        }
    }
}
```
### 复杂度分析
时间复杂度O(m*n)，空间复杂度O(max(m,n))