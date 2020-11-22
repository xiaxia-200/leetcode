## 274 H指数
### 解题思路
* H指数取值范围在1-citations.length之间，可以创建一个长度citations.length+1的新数组a记录引用次数i所对应的篇数，a[i]=k表示在这N篇文章中至少被引用了i次的文章有k篇。
* 使用两层循环找出每个i对应的篇数，并存入a[i]中
* 遍历a数组找到最大引用指数。
### 代码
```java
class Solution {
    public int hIndex(int[] citations) {
        int[] a = new int[citations.length+1];
        int max=0;
        for(int i=1; i<=citations.length; i++){
            int count=0;
            for(int num:citations){
                if(i<=num)
                    count++;
            }
            a[i]=count;
        } 
        for(int i=1; i<a.length; i++){
            if(i<=a[i] && i>max)
                max=i;
        }                 
        return max;   
    }
}
```
### 复杂度分析
时间复杂度O(n^2)，空间复杂度O(n)