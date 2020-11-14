## 442 数组中的重复元素
### 解题思路
* 数组元素范围在1-n之间，且要求算法的时间复杂度为O(n),不使用额外的空间，与448题的解题思想类似。数值的范围已经受到限制，因此可以利用数组下标对重复的元素进行标记
* 使用一次遍历扫描数组，假设得到的元素为num，则将下标为num-1的元素取反，如果该下标对应的元素已经是负数，则说明num是重复的元素，因此将其添加到列表中，最后列表中保存的元素就是重复元素。
### 代码
```java
class Solution {
    public List<Integer> findDuplicates(int[] nums) {
        List list = new ArrayList();
        int num;
        for(int i=0; i<nums.length; i++){
            if(nums[i]<0)
                num = -nums[i];
            else
                num = nums[i];
                
            if(nums[num-1]<0)
                list.add(num);
            else
                nums[num-1] = -nums[num-1];
        }
        return list;
    }
}
```
### 复杂度分析
时间复杂度O(N)，空间复杂度O(1)