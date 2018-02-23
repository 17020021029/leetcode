# Single Element in a sorted array
与[single number](https://leetcode.com/problems/single-number/description/)相同
## Problem
Given a sorted array consisting of only integers where every element appears twice except for one element which appears once. Find this single element that appears only once. 
## 分析
误戳，不知道注明找到这样一个medium难度的题，与easy的single number算法一致即能AC
## 代码实现
```ruby
int singleNonDuplicate(int* nums, int numsSize) {
    int result;
    for(int i=0;i<numsSize;i++)
    {
        result=result^nums[i];
    }
    return result;
}
```
## 总结
异或运算
