## 453 最小移动次数使数组元素相等
### 解题思路
* 题意又可以理解为：每次使一个元素不变，而让其他元素都增1，需要多少次才能使数组所有元素相等
* 让num[i]之外的所有元素加1相当于让num[i]减1，因此找出数组中最小的元素，计算出其他元素自减到最小值需要经历的总次数即可
### 代码
```java
class Solution {
    public int minMoves(int[] nums) {
        int min=Integer.MAX_VALUE;
        int sum1=0,sum2=0;
        int minMoves=0;
        for(int num:nums){
            if(num<min)
                min=num;
        }
        for(int num:nums){
            sum1+=num;
        }
        sum2=min*nums.length;
        return minMoves=sum1-sum2;
    }
}
```
### 复杂度分析
时间复杂度O(n)，空间复杂度O(1)