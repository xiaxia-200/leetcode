## 396 旋转函数
### 解题思路
每次将数组循环右移一位，得到F(K)的函数值，同时用max记录最大的函数值，进行了n-1次循环右移后，max中存的就是最终的最大值
### 代码
```java
class Solution {
    public int maxRotateFunction(int[] A) {
        int temp;
        int max = Integer.MIN_VALUE;
        if(A.length == 0)
            return 0;
        for(int i = 0; i < A.length; i++){
            if(i != 0){
                temp = A[A.length-1];
                for(int j = A.length-1; j>0; j--){
                    A[j] = A[j-1];                  
                }
                A[0] = temp;
            }          
            int count = 0;
            for(int j = 0; j < A.length; j++){
                count += j*A[j];
            }
            if(count > max)
                max = count;
        }
        return max;
    }
}
```
### 复杂度分析
时间复杂度O(n^2)，空间复杂度O(1)