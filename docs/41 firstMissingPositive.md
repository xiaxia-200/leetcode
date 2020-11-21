## 41 缺失的第一个正数
### 解题思路
* 最小正数的取值范围为1~nums.length+1,可以对现有的数组进行标记（元素取反）来找出最小的正数
* 对数组进行第一次遍历，将数组中的负数以及0赋值为数组长度+1，那么第二次遍历这些元素位置时就会直接跳过
* 对数组进行第二次遍历，如果数组元素nums[i]在1-nums.length之间，则将下标为nums[i]-1的数组元素取反，表明正数nums[i]已经存在；如果nums[i]为负数且它的的反数在以上范围之内，则表明该元素本身为正数只是被用作了标记，则将下标为-nums[i]-1的数组元素取反
* 最后一次遍历数组，遇到第一个为正的nums[i]就停下，最小正数即为i+1；若遍历结束没有遇到正数，则最小正数为数组长度+1
### 代
```java
class Solution {
    public int firstMissingPositive(int[] nums) {
        int min=0;
        for(int i=0; i<nums.length; i++){  
            if(nums[i]<=0)
                nums[i]=nums.length+1;
        }
        for(int i=0; i<nums.length; i++){ 
            if(nums[i]>0 && nums[i]<=nums.length){
                int k = nums[i];
                if(nums[k-1]>0)
                    nums[k-1]=-nums[k-1];
            }
            else if(nums[i]<0 && -nums[i]<=nums.length){
                int k = -nums[i];
                if(nums[k-1]>0)
                    nums[k-1]=-nums[k-1];
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