## 118 杨辉三角
### 解题思路
根据杨辉三角的特点，每一层的第一个和最后一个元素都为1，而中间的元素都是上一层相邻两个元素的和，可以通过for循环得到子列表的中间元素
### 代码
```java
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> result = new ArrayList<List<Integer>>();
        if(numRows==0) //层数为0时返回空列表
            return result;
        List<Integer> row1 = new ArrayList<Integer>();
        row1.add(1);
        result.add(row1); //第一层只有一个1元素
        for(int i=1; i<numRows; i++){ //根据层数建立其他子列表
            List<Integer> preRow = result.get(i-1);
            List<Integer> row = new ArrayList<Integer>();
            row.add(1); //第一个元素永远是1
            for(int j=0; j<i-1; j++){
                row.add(preRow.get(j)+preRow.get(j+1)); //中间的元素与上一层有关
            }
            row.add(1);
            result.add(row); //最后一个元素永远是1
        }
        return result;
    }
}
```
### 复杂度分析
时间复杂度O(n^2)，空间复杂度O(n)