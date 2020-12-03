## 283 移动零
### 解题思路
* 在不使用额外空间的情况下，将数组中所有的零移动到末尾，可以使用暴力解法。使用双层循环，当nums[i]=0时，就将i后面的元素往前移动一位，再将数组最后的元素赋值为0,同时用flag记录0的数量，当指针扫描到数组末尾第一个被移动的0元素时就跳出循环；如果nums[i]!=0，则指针后移，继续扫描其他元素。
### 代码
```java
class Solution {
    public void moveZeroes(int[] nums) {
        int flag = 0;
        for(int i=0; i<nums.length-1;){
            if(i == nums.length-flag)
                break;
            else if(nums[i]==0){
                for(int j=i+1; j<nums.length; j++){
                    nums[j-1]=nums[j];
                }
                nums[nums.length-1]=0;
                flag++;
            }
            else
                i++;
        }
    }
}
```
### 复杂度分析
时间复杂度O(N^2)，空间复杂度O(1)