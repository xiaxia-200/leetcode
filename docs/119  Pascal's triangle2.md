## 杨辉三角2
### 解题思路
返回rowIndex层的列表，并且空间复杂度为O(n)。与118解题思路类似，不同的是利用了preRow保存上一层的列表，不用将每层的列表都保存下来
### 代码
```java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        ArrayList<Integer> preRow = new ArrayList<Integer>();
        ArrayList<Integer> Row = new ArrayList<Integer>();
        preRow.add(1);
        if(rowIndex==0)
            return  preRow;
        for(int i=1; i<=rowIndex; i++){
            Row.add(1);
            for(int j=0; j<i-1; j++){
                Row.add(preRow.get(j)+preRow.get(j+1));
            }
            Row.add(1);
            preRow = (ArrayList<Integer>) Row.clone();
            if(i!=rowIndex)
                Row.clear();
        }
        return Row;
    }
}
```
### 复杂度分析
时间复杂度O(n^2)，空间复杂度O(n)