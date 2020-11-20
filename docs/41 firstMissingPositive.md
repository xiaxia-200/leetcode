## 41 缺失的第一个正数
### 解题思路
* 数组的最小正数取值范围为1~nums.length,可以对现有的数组进行标记（元素取反）来找出最小的正数
* 对数组进行第一次遍历，将数组中的负数赋值为0，那么第二次遍历到负数位置时就会直接跳过；将0赋值为其下标数+1，遍历到0元素时
* 对数组进行第二次遍历，如果数组元素为nums[i]在最小正数的取值范围之内，则将下标为nums[i]-1的数组元素取反（前提：该下标对应元素不等于0，即本身不是负数。如果对应元素为0，则将元素值赋为数组长度+1的负数，避免下次扫描到该元素时，再对该元素进行变动），表明正数nums[i]已经存在；如果nums[i]为负数，则检查该元素的反数是否在最小正数范围之内，若是，则对该元素进行和以上相同的标记
* 最后一次遍历数组，根据标记找出最小正数
### 代码
```java
class Solution {
    public int firstMissingPositive(int[] nums) {
        int min=0;
        for(int i=0; i<nums.length; i++){  
            if(nums[i]<0)
                nums[i]=0;
            if(nums[i]==0)
                nums[i]=i+1;
        }
        for(int i=0; i<nums.length; i++){ 
            if(nums[i]>0 && nums[i]<=nums.length){
                    int k = nums[i];
                    if(nums[k-1]>0)
                        nums[k-1]=-nums[k-1];
                    else if(nums[k-1]==0)
                        nums[k-1]=-nums.length-1;
            }
            else if(nums[i]<0){
                if(-nums[i]<=nums.length){
                    int k = -nums[i];
                    if(nums[k-1]>0)
                        nums[k-1]=-nums[k-1];
                    else if(nums[k-1]==0)
                        nums[k-1]=-nums.length-1;
                }
            }
        }
        for(int i=0; i<nums.length; i++){
            if(nums[i]>0){
                min = i+1;
                break;
            }
        }
        if(min>0)
            return min;
        else{
            min=nums.length+1;
            return min;
        }          
    }
}
```
### 复杂度分析
时间复杂度O(N)，空间复杂度O(1)