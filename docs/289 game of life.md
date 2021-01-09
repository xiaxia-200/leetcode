## 289 生命游戏
### 解題思路
使用特殊标记进行原地变换，扫描二维数组检查其周围的细胞状态，记录活细胞的个数，如果活细胞个数小于2或者大于3那么该细胞就死亡，如果周围的活细胞数等于3那么死细胞存活。对细胞将要改变的状态进行标记，如果是复活则将其变为-1,否则标记为2。最后一次对数组的扫描过程中再将要变动的细胞重新置为0或1 
### 代码
```java
class Solution {
    public void gameOfLife(int[][] board) {
        int m = board.length;
        int n = board[0].length;
        int[] Dx = new int[] {0,0,1,-1,1,-1,1,-1};
        int[] Dy = new int[] {1,-1,0,0,-1,-1,1,1};
        for(int i = 0; i < m; i++){
            for(int j = 0; j < n; j++){
                int sum = 0;//记录检测细胞周围活细胞的个数
                //检测细胞周围的活细胞
                for(int k = 0; k < 8; k++){
                    int x = i + Dx[k];
                    int y = j + Dy[k];
                    if(x < 0 || x >= m || y < 0 || y >=n)
                        continue;
                    if(board[x][y] > 0)
                        sum++;
                }
                //判断细胞存活与否
                if(board[i][j] == 0){
                    if(sum ==3)
                        board[i][j] = -1;//将要复活的细胞标记为-1，第二次扫描数组事再将其置为1
                }
                if(board[i][j] == 1){
                    if(sum < 2 || sum >= 4)
                        board[i][j] = 2;//将要死亡的细胞标记为2，第二次扫描数组时再将其置为0
                }
            }
        }
        for(int i = 0; i < m; i++){
            for(int j = 0; j < n; j++){
                if(board[i][j] == -1)
                    board[i][j] = 1;
                if(board[i][j] == 2)
                    board[i][j] = 0;
            }
        }
    }
}
```
### 复杂度分析
时间复杂度O(m*n)，空间复杂度O(1)