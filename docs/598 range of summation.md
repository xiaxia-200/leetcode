## 598 范围求和2
### 解题思路一
暴力解法：将二维数组中的元素按照要求增1，操作完之后，最大的数值为二维数组的第一个元素，遍历二维数组找出最大元素的个数
### 代码
```java
public class Solution {
    public int maxCount(int m, int n, int[][] ops) {
        int[][] result = new int[m][n];
        for (int[] op: ops) {
            for (int i = 0; i < op[0]; i++) {
                for (int j = 0; j < op[1]; j++) {
                    result[i][j] += 1;
                }
            }
        }
        int maxCount = 0;
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (result[i][j] == result[0][0])
                    maxCount++;
            }
        }
        return maxCount;
    }
}
```
### 复杂度分析
时间复杂度0(m*n),空间复杂度O(m*n)
### 解题思路二
检测最大元素的个数并不需要建立新的二维数组，因为元素的变化与ops中的操作有关，只要根据ops检查出每次都会发生变化的范围就可以得出最大元素个数
### 代码
```java
class Solution {
    public int maxCount(int m, int n, int[][] ops) {
        int maxCount = 0;
        if(ops==null)
            return maxCount;

        int p = m;
        int q = n;

        //检测每次元素都会发生改变的行与列
        for(int[] op:ops){
            if(op[0]<p)
                p=op[0];
            if(op[1]<q)
                q=op[1];
        }
        maxCount = p*q;
        return maxCount;
    }
}
```
### 复杂度分析
时间复杂度O(N)，空间复杂度O(1)；N为ops数组中元素的个数