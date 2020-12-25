## 498 对角线遍历
### 解题思路
* 当二维数组的只有一行或者一列的时候，按照原顺序输出数组
* 其他情况，可以根据扫描次数i(i从0开始计算)来组织遍历元素的顺序。当扫描次数为i时，本次扫描的所有元素(x,y)其横纵坐标值和x+y==i,且本轮第一个扫描到的元素其横坐标x或者纵坐标y都会尽可能取最大值（当i小于行数或列数时，x或y的最大值为i；当i大于行数m或列数n时，x最大值为m-1，y的最大值为n-1）。
* 偶数次扫描时，x坐标尽可能取得最大值，进入本轮的for循环进行赋值，y坐标的值根据i和x确定，result[k]=matrix[x][y]
* 奇数次扫描时，y坐标尽可能取得最大值，进入本轮的for循环进行赋值，x坐标的值根据i和y确定，result[k]=matrix[x][y]
* 进行m+n-1次扫描后，就完成了所有元素的遍历，结果保存在result中
### 代码
```java
class Solution {
    public int[] findDiagonalOrder(int[][] matrix) {
        int m = matrix.length;
        if(m == 0) //数组为空则返回空
            return new int[0];

        int n = matrix[0].length;

        if(m == 1){ //当二维数组只有一行时，直接按原顺序输出
            int[] result = new int[n];
            for(int i = 0; i < n; i++)
                result[i] = matrix[0][i];
            return result;
        }
        
        if(n == 1){ //当二维数组只有一列时，直接按原顺序输出
            int[] result = new int[m];
            for(int i = 0; i < m; i++)
                result[i] = matrix[i][0];
            return result;
        }

        int k = 0;
        int[] result = new int[m*n];

        for(int i = 0; i < m+n-1; i++){ //箭头遍历的次数为m+n-1次
            if(i % 2 == 0){ //偶数次遍历时箭头向下，(x,y)的x坐标从能取到的最大值递减，并确保
                if( i < m ){ 
                    for(int x = i; x >-1 && x >i-n; x--){ //由于y的值最大取n-1, x=i-y=i-n+1,因此 x>i-n,且同时要满足横坐标大于等于0
                        int y = i - x;
                        result[k++] = matrix[x][y];
                    }
                }
                else{
                    for(int x = m-1; x > -1 && x > i-n; x--){
                        int y = i - x;
                        result[k++] = matrix[x][y];
                    }
                }              
            }
            else{ //奇数次遍历时箭头向上，(x,y)的y坐标从能取到的最大值递减
                if(i < n){
                    for(int y = i; y > -1 && y > i-m; y--){//由于x的值最大取m-1, y=i-x=i-m+1,因此 y>i-m,且同时要满足纵坐标大于等于0
                        int x = i - y;
                        result[k++] = matrix[x][y];
                    }
                }
                else{
                    for(int y = n-1; y > -1 && y > i-m; y--){
                        int x = i - y;
                        result[k++] = matrix[x][y];
                    }
                }
            }
        }
        return result;
    }
}
```
### 复杂度分析
时间复杂度O(m*n)，空间复杂度O(m*n)