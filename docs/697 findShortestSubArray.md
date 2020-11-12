## 697 数组的度
### 解题思路
使用双重循环找出数组中度数最大的数，同时使用m,n记录该数出现的始末位置，m与n之间的长度就是数组最短连续子数组的长度
### 代码
```java
class Solution {
    public int findShortestSubArray(int[] nums) {
        int m=0,n=0;//分别记录ij的位置
        int p=0,q=0;//p记录最大度数,q记录每次扫描时的度数
        int max=0;//记录最小子数组的长度
        int k=0;//k用于记录数组中是否有重复元素
        for(int i=0;i<nums.length;i++){
            q=0;
            n=i;
            for(int j=i+1;j<nums.length;j++){
                if(nums[i]==nums[j]){
                    q++;
                    n=j;
                    k++;
                }
            }
            if(q>p){
                p=q;
                m=i;
                max=n-m+1;
            }
            else if(q==p&&nums[m]!=nums[n]){ //如果出现度相同的元素，则比较包含他们的子数组哪个更短
                if(n-i+1<max){
                    m=i;
                    max=n-i+1;
                }
            }
        }
        if(k==0) //如果数组中没有重复元素，则最小的度为1
            max=1;
        return max;
    }
}
```
### 复杂度分析
时间复杂度O(N^2)，空间复杂度O(1)