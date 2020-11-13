## 448 找到数组中消失的元素
### 解题思路
* 题目要求不能使用额外空间，因此想要时间复杂度为O(n)只能在已有的空间上进行修改，利用数组的下标来对已有元素进行标记
* 依次扫描数组元素，假设元素数值为k，则将下标为k-1的元素取反（前提：该下标的元素本来就不是负数。若已经是负数，说明k是重复的数值，该下标对应元素不需改动）
* 再次扫描数组，假设下标为i，若nums[i]不是负数，则说明i+1数值缺失，将该数值添加到列表
* 缺失数值添加完毕，输出列表
### 代码
```java
class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        List<Integer> list = new ArrayList();
        for(int num:nums){
            if(num>0){
                if(nums[num-1]>0)
                    nums[num-1] = -nums[num-1];
            }
            else{
                int k = -num;
                if(nums[k-1]>0)
                    nums[k-1] = -nums[k-1];
            }
        }
        for(int i=0; i<nums.length; i++){
            if(nums[i]>0)
                list.add(i+1);
        }
        return list;
    }
}
```
### 复杂度分析
时间复杂度O(N),空间复杂度O(1)