# Romove Element
删除元素
## 题目描述
Given an array and a value, remove all instances of that value in-place and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.
## 分析&解题思路
题目要求是删除数组中的元素，然后返回新数组的长度，不能新开数组，那么可以通过替换元素得到新数组。返回数组长度：因为上一步只是对元素的替换，数组长度不变，不可以用sizeof函数求数组长度，那么可以申请整型来记录替换的数组元素个数。。

## 代码实现
```
int removeElement(int* nums, int numsSize, int val) {
    if(numsSize==0)
        return 0;
    int sum=0;
    for(int i=0;i<numsSize;i++)
    {
        if(*(nums+i)!=val){
            *(nums+sum)=*(nums+i);
            sum++;
        }
    }
    return sum;
}
```
## 总结
无非是对数组的处理，注意解题思路就好
