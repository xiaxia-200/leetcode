## 螺旋矩阵2
### 解题思路
与54题解题思路一致，在界线范围内重复顺时针扫描操作，同时将元素赋予对应的值，每次移动值增一，当出现界限交互时就说明组建完成，输出数组即可
### 代码
```java
class Solution {
    public int[][] generateMatrix(int n) {
        int[][] matrix = new int [n][n];
        int num = 0;
        //设置上下左右边界
        int a = 0;//上
        int b = n-1;//下
        int c = 0;//左
        int d = n-1;//右

        while(true){
            for(int i = c; i <= d; i++) //向右
                matrix[a][i] = ++num;
            if(++a > b) //上界改变
                break;
            for(int i = a; i <= b; i++)//向下
                matrix[i][d] = ++num;
            if(--d < c)//右界改变
                break;
            for(int i = d; i >= c; i--)//向左
                matrix[b][i] = ++num;
            if(--b < a)//下界改变
                break;
            for(int i = b; i >=a; i--)//向上
                matrix[i][c] = ++num;
            if(++c > d)//左界改变
                break;
        }
        return matrix;
    }
}
```
### 复杂度分析
时间复杂度O(n^2)，空间复杂度O(n^2)