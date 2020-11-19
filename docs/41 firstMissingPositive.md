## 41 缺失的第一个正数
### 解题思路

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