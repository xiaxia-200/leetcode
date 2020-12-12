## 419 甲板上的船舰
### 解题思路
当board[i][j]==‘X’的左边或者上边有‘X’存在时，说明board[i][j]位于船舰的中间位置，因此可以直接跳过，否则需要将船舰数量加1
### 代码
```java
class Solution {
    public int countBattleships(char[][] board) {
        int count = 0;
        for(int i = 0; i < board.length; i++){
            for(int j = 0; j < board[0].length; j++){
                if(board[i][j] == '.')
                    continue;
                if(i > 0 && board[i-1][j] == 'X')
                    continue;
                if(j > 0 && board[i][j-1] == 'X')
                    continue;
                count++;
            }
        }
        return count;
    }
}
```
### 复杂度分析
时间复杂度O(N)，空间复杂度O(1).其中N为二维数组元素的个数