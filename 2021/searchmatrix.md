# 搜索二维矩阵

编写一个高效的算法来搜索 m x n 矩阵 matrix 中的一个目标值 target 。该矩阵具有以下特性：

每行的元素从左到右升序排列。
每列的元素从上到下升序排列。

## 代码
```
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        int col = 0, row = matrix.size() - 1;
        while(row >= 0 && col < matrix[0].size()){
            if(target > matrix[row][col]){
                col++;
            }else if(target < matrix[row][col]){
                row--;
            }else{
                return true;
            }
        }
        return false;
    }
};
```
## 运行结果
用时164ms，也太长了点吧。。。
等下再用二分法试一下

## 考察方法
### 分治算法
把大的问题转换为小的问题解决
### 二分算法
分治算法的一种特例
## 待改结果
想用二分法做的一道题，但是超时了，明天再改
```
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        int high = matrix[0].size()-1, low= 0;
        int index = (high+low)/2;
        for (int i=0;i<matrix.size();){
            if(matrix[i][0]<target){
                i++;
            }
            else{
            index=(high+low)/2;
            if(matrix[i][index] < target){
                low=index+1;
            }
            else if (matrix[i][index] > target){
                high = index-1;
            }
            else return true;
        }
        }
        return false; 
    }
};
```
