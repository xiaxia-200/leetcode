## 665 非递减数列
### 解题思路
* 在最多只改变一个元素的条件下，将数组变成非递减数组，则需要遇到第一个nums[i]>nums[i+1]时就对元素进行改动，之后再对数组进行非递减判定
* 第一个不满足条件的元素nums[i]之前的元素都符合非递减条件，因此在对元素进行改动时只有两种选择情况，即对nums[i]或者nums[i+1]进行改变，将其赋值为前一个元素的值，只要保证改变之后nums[i-1],nums[i],nums[i+1]能满足非递减规则即可
* 第一次改动之后就结束本轮的数组遍历，并对数组进行第二次遍历，如果所有元素都满足非递减规则，则返回true
### 代码
```java
class Solution {
    public boolean checkPossibility(int[] nums) {
        for(int i=0; i<nums.length-1; i++){
            if(nums[i]>nums[i+1]){
                if(i>0){
                    int k = nums[i-1];
                    if(k<=nums[i+1]){
                        nums[i] = nums[i-1];
                        break;
                    }
                    else{
                        nums[i+1] = nums[i];
                        break; 
                    }
                    
                }
                else{
                    nums[i] = nums[i+1];
                    break;
                }
            }
        }
        for(int i=0; i<nums.length-1; i++){
            if(nums[i]>nums[i+1])
                return false;
        }
        return true;
    }
}
```
### 复杂度分析
时间复杂度O(N)，空间复杂度O(1)