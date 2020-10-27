## 495  提莫攻击
### 方法一：解题思路
* 循环遍历数组，得出每两次相邻攻击时间的时间差。
* 如果时间差小于中毒持续时间duration，则总持续时间只需要加上该时间差
* 如果时间差大于或等于中毒持续时间duration，则总持续时间需加上duration
* 最后一次攻击一定会持续duration时间长，因此当至少有一次攻击时，总持续时间需加上最后一次攻击中毒时间
### 代码
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
### 复杂度分析
时间复杂度O(N),空间复杂度O(1)

### 方法二：解题思路
首先假设攻击时间间隔都大于中毒持续时长duration，得出在该情况下的总中毒持续时间totalDuration。循环遍历数组，得出相邻两次攻击之间的时间间隔，若小于中毒持续时间duration，则使用k记录多计算在totalration中的时间。最后totalDuration减去k就得到最终的中毒持续时间。
### 代码
```
class Solution {
    public int findPoisonedDuration(int[] timeSeries, int duration) {
        int totalDuration;
        int k=0;
        totalDuration = timeSeries.length*duration;
        for(int i=0; i < timeSeries.length-1; i++){
            int m = timeSeries[i+1] - timeSeries[i];
            if(m < duration){
                k += (duration - m);
            }
        }
        totalDuration -= k;
        return totalDuration;
    }
}
```
### 复杂度分析
时间复杂度O(N),空间复杂度O(1) 