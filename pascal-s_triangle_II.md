# Pascal's Triangle II
similar:[Pascal's Triangle](https://github.com/17020021029/leetcode/blob/master/pascal's_triangle.md)
## Problem
Given an index k, return the kth row of the Pascal's triangle.</br>
For example, given k = 3,</br>
Return [1,3,3,1].</br>
Note:</br>
Could you optimize your algorithm to use only O(k) extra space?</br>
## 分析
原理还是杨辉三角，但只需返回给给定行的数组，需要返回数组长度
## 代码实现
```ruby
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* getRow(int rowIndex, int* returnSize) {
    int *result;
    result=(int*)malloc(sizeof(int)*(rowIndex+1));
    int i=0,j=0;
    for(i=0;i<=rowIndex;i++)
    {
        for(j=i;j>=0;j--) //逆序
        {
            if(0==i||i==j)
                result[j]=1;
            else 
                result[j]=result[j]+result[j-1];
        }
    }
    *returnSize=rowIndex+1;
    return result;
}
```
## 总结
1. 数组动态内存分配
2. 两层循环，第一层代表行数，第二层代表列数
3. 此算法涉及数组元素的替换，内层循环需要逆序遍历，否则会改变要相加的元素
