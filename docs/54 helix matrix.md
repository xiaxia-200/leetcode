## 54 螺旋矩阵
### 解题思路
顺时针方向扫描二维数组得到螺旋矩阵，可以定义扫描时的上下左右边界，在这个界限内重复顺时针移动操作，当出现边界交互的时候就说明已经扫描完所有元素
### 代码
```java
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> result = new ArrayList<Integer>();
        //m、n为上下界，p、q为左右界
        int m = 0;
        int n = matrix.length-1;
        int p = 0;
        int q = matrix[0].length-1;
        
        while(true){ //当界限交互的时候说明已经扫描完所有元素，跳出循环
            for(int i = p; i <= q; i++) //向右
                result.add(matrix[m][i]);
            if(++m > n)//上边界改变
                break;
            for(int i = m; i <= n; i++)//向下
                result.add(matrix[i][q]);
            if(--q < p)//右边界改变
                break;
            for(int i = q; i >= p; i--)//向左
                result.add(matrix[n][i]);
            if(--n < m)//下边界改变
                break;
            for(int i = n;  i >=m; i--)//向上
                result.add(matrix[i][p]);
            if(++p > q)//左边界改变
                break;
        }

        return result;
    }
}
```
### 复杂度分析
时间复杂度O(m*n)，空间复杂度O(m*n).m n分别是矩阵的行数和列数