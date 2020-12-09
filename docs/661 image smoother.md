## 661 图片平滑器
### 解题思路
题意：每个元素的灰度是所有与它相邻的元素和的平均值（包含本身）
暴力解法，遍历数组，查看每个元素的四周是否存在相邻元素，并用sum记录所有相邻元素的和，用count记录相邻元素的个数
### 代码
```java
class Solution {
    public int[][] imageSmoother(int[][] M) {
        int m = M.length;//行数
        int n = M[0].length;//列数
        int[][] result = new int[m][n];
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                int sum = M[i][j];
                int count = 1;
                //同一行是否有相邻元素存在
                if(j-1 >= 0){
                    sum += M[i][j-1];
                    count++;
                }
                if(j+1 < n){
                    sum += M[i][j+1];
                    count++;
                }
                //上一行是否有相邻元素存在
                if(i-1 >= 0){
                    sum += M[i-1][j];
                    count++;
                    if(j-1 >= 0){
                        sum += M[i-1][j-1];
                        count ++;
                    }                       
                    if(j+1 < n){
                        sum += M[i-1][j+1];
                        count ++;
                    }                        
                }
                //下一行是否有相邻元素存在
                if(i+1 < m){
                    sum += M[i+1][j];
                    count++;
                    if(j-1 >= 0){
                        sum += M[i+1][j-1];
                        count++;
                    }                       
                    if(j+1 < n){
                        sum += M[i+1][j+1];
                        count++;
                    }       
                }
                result[i][j] = sum/count;
            }
        }
        return result;
    }
}
```
### 代码优化
```java
class Solution {
    public int[][] imageSmoother(int[][] M) {
        int m = M.length;//行数
        int n = M[0].length;//列数
        int[][] result = new int[m][n];
        for(int i=0; i<m; i++){
            for(int j=0; j<n; j++){
                int count=0;
                for(int p=i-1; p<=i+1; p++){
                    for(int q=j-1; q<=j+1; q++){
                        if(p>=0 && p<m && q>=0 && q<n){
                            result[i][j] += M[p][q];
                            count++;
                        }
                    }
                }
                result[i][j] /= count;
            }
        }
        return result;
    }
}
```
### 复杂度分析
时间复杂度O(N)，空间复杂度O(N).其中N为二维数组中元素的个数