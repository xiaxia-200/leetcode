## 628 三个数的最大乘积
### 解题思路
数组中元素有正有负，求三个数的最大乘积只需找出最大的三个数以及最小的两个数，再比较两个乘积的大小即可
### 代码
```java
public class Solution {
    public int maximumProduct(int[] nums) {
        int min1 = Integer.MAX_VALUE, min2 = Integer.MAX_VALUE;
        int max1 = Integer.MIN_VALUE, max2 = Integer.MIN_VALUE, max3 = Integer.MIN_VALUE;
        for (int n: nums) {
            if (n <= min1) {
                min2 = min1;
                min1 = n;
            } else if (n <= min2) {    
                min2 = n;
            }
            if (n >= max1) {          
                max3 = max2;
                max2 = max1;
                max1 = n;
            } else if (n >= max2) {  
                max3 = max2;
                max2 = n;
            } else if (n >= max3) {     
                max3 = n;
            }
        }
        return Math.max(min1 * min2 * max1, max1 * max2 * max3);
    }
}
```
### 复杂度分析
时间复杂度O(N)，空间复杂度O(1)
