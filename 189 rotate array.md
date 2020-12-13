## 189 旋转数组
### 解题思路
每次右移一位，利用x来存储数组最后一个元素，将数组中的每个元素向右移动一位后将x赋值给nums[0]，如此重复k次之后就完成了循环右移k位
### 代码
```java
class Solution {
    public void rotate(int[] nums, int k) {
        int x;
        for(int i = 0; i<k; i++){
            x = nums[nums.length-1];
            for(int j = nums.length-1; j>0; j--){
                nums[j] = nums[j-1];
            }
            nums[0] = x;
        }
    }
}
```
### 复杂度分析
时间复杂度O(k*n)，空间复杂度O(1)