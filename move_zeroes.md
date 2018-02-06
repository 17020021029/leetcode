# [Move Zeroes](https://leetcode.com/problems/move-zeroes/description/)
[Romove Element](https://github.com/17020021029/leetcode/blob/master/review_remove_element.md)的变式
## 题目描述
 Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0].

Note:

    You must do this in-place without making a copy of the array.
    Minimize the total number of operations.
## 分析&解题思路
这道题与romove elemnt类似，这个直接是数组的代换，不过还要把被替换掉的数组再加到数组后面，可以记录上一步替换的元素个数，然后从这个开始遍历，将数组元素赋值为0

## 代码实现
```
void moveZeroes(int* nums, int numsSize) {
    if(numsSize==0)
        return nums;
    int sum=0;
    for(int i=0;i<numsSize;i++)
    {
        if(*(nums+i)!=0)
        {
            *(nums+sum)=*(nums+i);
            sum++;
        }
    }
    for(int j=sum;j<numsSize;j++)
    {
        *(nums+j)=0;
    }
    return nums;
}
```
## 总结
虽说时间有限，先接触题型重要，但想我这种木有天赋的还是复习一下子的好
