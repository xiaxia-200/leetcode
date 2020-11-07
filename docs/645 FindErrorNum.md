## 错误的集合
### 解题思路
先使用两层循环找出重复的元素，并得到出错数组的元素总和，由于在数据没有发生错误的情况下，数组元素的总和应该为从1到数组长度数值的连续和，因此得出正确数组总和后，减去错误数组元素总和以及重复元素值，就可以得到出错元素值。
### 代码
```java
class Solution {
    public int[] findErrorNums(int[] nums) {
        int k=0;
        int i=0;
        int sum1=0,sum2=0;
        int[] arr = new int [2];
        for(;i<nums.length;i++){
            for(int j=i+1;j<nums.length;j++){
                if(nums[i]==nums[j]){
                    k=1;
                    break;
                }
            }
            if(k==1){
                break;
            }
        }
        arr[0]=nums[i];
        for(int num:nums)
            sum1+=num;
        for(int j=1;j<=nums.length;j++)
            sum2+=j;
        sum1-=nums[i];
        arr[1]=sum2-sum1;
        return arr;
    }
}
```
### 复杂度分析
时间复杂度O(N^2),空间复杂度O(1)