# Next Permutation
## Problem 
Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers.

If such arrangement is not possible, it must rearrange it as the lowest possible order (ie, sorted in ascending order).

The replacement must be in-place, do not allocate extra memory.

Here are some examples. Inputs are in the left-hand column and its corresponding outputs are in the right-hand column.
1,2,3 → 1,3,2
3,2,1 → 1,2,3
1,1,5 → 1,5,1
## 问题分析
问题实际就是将数组看做整数，通过替换元素找到比原数大的但又是其中最小的数；若没有，则升序排列；所以这道题只需要逆序遍历即可

## 代码实现
```ruby
void nextPermutation(int* nums, int numsSize) {
    int i=numsSize-1;
    int j;
    while(i>0 && nums[i]<=nums[i-1])
        i--;
    int temp;
    if(i>0)
    {
        j=numsSize-1;
        while(j>=i && nums[j]<=nums[i-1])
            j--;
        temp=nums[j];
        nums[j]=nums[i-1];
        nums[i-1]=temp;
    }
    j=numsSize-1;
    //这种情况输入的数组是降序的，所以正好倒转
        while(i<j)
        {
            temp=nums[i];
            nums[i]=nums[j];
            nums[j]=temp;
            i++;j--;
        }
}
```
