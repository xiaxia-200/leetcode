## 414 第三大的数
### 解题思路
* 使用first,second,third来记录前三大的数字，由于数组非空一定有最大值，因此将first赋初值为nums[0],而将second和third赋初值为负无穷。
* 循环遍历数组，如果数组元素大于first，则将该数值赋给first，而将原本first的值赋给second，将原本second的值赋给third，依此类推
* 最后如果third不等于负无穷则返回该第三大的值，否则返回数组最大值。
### 代码
```java
class Solution {
    public int thirdMax(int[] nums) {
        int first = nums[0];
        long second = Long.MIN_VALUE;
        long third = Long.MIN_VALUE;
        for (int num : nums) {
            if(num>first){
                third = second;
                second = first;
                first = num;
            }else if(num>second&&num<first){
                third = second;
                second = num;
            }else if(num<second&&num>third){
                third = num;
            }
        }
        if (third==Long.MIN_VALUE)
            return first;
        else
            return (int)third;
    }
}
```
### 复杂度分析
时间复杂度O(N),空间复杂度O(1)