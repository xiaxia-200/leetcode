# 495  提莫攻击
## 解题思路
* 循环遍历数组，得出每两次相邻攻击时间的时间差。
* 如果时间差小于中毒持续时间duration，则总持续时间只需要加上该时间差
* 如果时间差大于或等于中毒持续时间duration，则总持续时间需加上duration
* 最后一次攻击一定会持续duration时间长，因此当至少有一次攻击时，总持续时间需加上最后一次攻击中毒时间
## 代码
```java
class Solution {
    public int findPoisonedDuration(int[] timeSeries, int duration) {
        int totalDuration=0;
        for(int i=0; i < timeSeries.length-1; i++){
            int j = i + 1;
            int m = timeSeries[j]-timeSeries[i];
            if(m < duration){
                totalDuration+=m;
            }
            else{
                totalDuration+=duration;
            }
        }
        if(timeSeries.length > 0){
            totalDuration+=duration;
        }
        return totalDuration;
    }
}
```
## 复杂度分析
时间复杂度O(N),空间复杂度O(1)