# Remove Duplicates from Sorted Array
数组的处理
## Problem
Given a sorted array, remove the duplicates in-place such that each element appear only once and return the new length.</br>
Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.
## 分析&解题思路
题目要求把数组中重复的元素，然后返回数组的长度</br>
因为数组是顺序的，所以遍历数组时只需要遍历一次就好</br>
题目要求不能重开数组，所以只能再遍历时对数组重新赋值，若与前一个不相同，给数组赋值，否则不赋值，最后一个数组的下标加一即为数组的长度
## 代码实现
```ruby
int removeDuplicates(int* nums, int numsSize) {
    int i=0;
    if(numsSize==0)
        return 0;
    for(int j=0;j<numsSize;j++)
    {
        if(*(nums+i)!=*(nums+j))
        {
            i++;
            *(nums+i)=*(nums+j);
        }
    }
    return i+1;
}
```
## 总结
类似解法的题目之前做过，遍历的过程中直接将数组元素替换，避免重开数组
