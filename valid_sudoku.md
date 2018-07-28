## Problem
Determine if a 9x9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules:

Each row must contain the digits 1-9 without repetition.
Each column must contain the digits 1-9 without repetition.
Each of the 9 3x3 sub-boxes of the grid must contain the digits 1-9 without repetition.

A partially filled sudoku which is valid.

The Sudoku board could be partially filled, where empty cells are filled with the character '.'.

Example 1:

Input:
[
  ["5","3",".",".","7",".",".",".","."],
  ["6",".",".","1","9","5",".",".","."],
  [".","9","8",".",".",".",".","6","."],
  ["8",".",".",".","6",".",".",".","3"],
  ["4",".",".","8",".","3",".",".","1"],
  ["7",".",".",".","2",".",".",".","6"],
  [".","6",".",".",".",".","2","8","."],
  [".",".",".","4","1","9",".",".","5"],
  [".",".",".",".","8",".",".","7","9"]
]
Output: true
Example 2:

Input:
[
  ["8","3",".",".","7",".",".",".","."],
  ["6",".",".","1","9","5",".",".","."],
  [".","9","8",".",".",".",".","6","."],
  ["8",".",".",".","6",".",".",".","3"],
  ["4",".",".","8",".","3",".",".","1"],
  ["7",".",".",".","2",".",".",".","6"],
  [".","6",".",".",".",".","2","8","."],
  [".",".",".","4","1","9",".",".","5"],
  [".",".",".",".","8",".",".","7","9"]
]
Output: false
Explanation: Same as Example 1, except with the 5 in the top left corner being 
    modified to 8. Since there are two 8's in the top left 3x3 sub-box, it is invalid.
Note:

A Sudoku board (partially filled) could be valid but is not necessarily solvable.
Only the filled cells need to be validated according to the mentioned rules.
The given board contain only digits 1-9 and the character '.'.
The given board size is always 9x9.
## 解题思路
要解这道题，首先要了解数独的规则，在题目中都有解释</br>
题目的墓地是让我们判断是否是有解的题目，只要按照最终形成的期盼判断即可
## 代码实现
我用到是最简单的便利的办法
```C++
class Solution {
public:
    bool isValidSudoku(vector<vector<char>>& board) {
        int size=board.size();
        vector<int> count;
        //检查每行
        for(int i=0;i<size;i++){
            count.assign(9,0);
            for(int j=0;j<size;j++){
                if(board[i][j]!='.'){
                    int tmp=board[i][j]-'1';
                    if(count[tmp]>0)
                        return false;
                    else
                        count[tmp]++;
                }
                else continue;
            }
        }
        //检查每列
        for(int j=0;j<size;j++){
            count.assign(9,0);
            for(int i=0;i<size;i++){
                if(board[i][j]!='.'){
                    int tmp=board[i][j]-'1';
                    if(count[tmp]>0)
                        return false;
                    else
                        count[tmp]++;
                }
                else continue;
            }
        }
        //检查每个小格
        for(int i=0;i<size;i+=3){
            for(int j=0;j<size;j+=3){
                count.assign(9,0);
                for(int row=i;row<i+3;row++){
                    for(int col=j;col<j+3;col++){
                        if(board[row][col]!='.'){
                            int tmp=board[row][col]-'1';
                            if(count[tmp]>0)
                                return false;
                            else 
                                count[tmp]++;
                        }
                        else continue;
                    }
                }
            }
        }
        return true;
    }
};
```
