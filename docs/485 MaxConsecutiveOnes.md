## 485 最大连续1的个数
### 方法一：解题思路
设置两个指针，i保存每次开始扫描的位置，j为工作指针，使用maxCount记录最大连续1的个数。遍历数组，如果数组元素为1则j指针后移，否则将两指针位置比较得出本次连续1的个数，并将i指针位置更新，开始新一轮扫描。
### 代码
```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int i = 0;
        int j = 0;
        int m = nums.length;
        int maxCount = 0;
        while(i<m && j<m){
            while(nums[j]==1){
                if(j<m-1)
                    j++;
            }
            int k = j-i+1;
            i = j;
            if(k>maxCount)
                maxCount=k;
        }
        return maxCount;
    }
}
```
### 复杂度分析
时间复杂度O(N),空间复杂度O(1)

### 方法二：解题思路
数组长度为1时，最大连续1的个数和元素数值相同；当数组长度大于1时，遍历数组，当数组元素nums[i]等于1时，进入while循环，检测从i位置开始，连续1的个数。
### 代码
```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int max = 0;
        if(nums.length==1){
            max = nums[0];
        }
        else{
            for(int i = 0; i < nums.length; i++){
                int j = 0;
                while(nums[i] == 1){
                    j++;
                    if(i < nums.length-1)
                        i++;
                    else
                        break;
                }
                if(j>=max)
                   max = j;
            }
        }

    return max;
    }
}
```
### 复杂度分析
时间复杂度O(N),空间复杂度O(1)