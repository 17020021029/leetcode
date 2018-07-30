## problem
Given a sorted array nums, remove the duplicates in-place such that duplicates appeared at most twice and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

Example 1:

Given nums = [1,1,1,2,2,3],

Your function should return length = 5, with the first five elements of nums being 1, 1, 2, 2 and 3 respectively.

It doesn't matter what you leave beyond the returned length.
Example 2:

Given nums = [0,0,1,1,1,1,2,3,3],

Your function should return length = 7, with the first seven elements of nums being modified to 0, 0, 1, 1, 2, 3 and 3 respectively.

It doesn't matter what values are set beyond the returned length.
Clarification:

Confused why the returned value is an integer but your answer is an array?

Note that the input array is passed in by reference, which means modification to the input array will be known to the caller as well.

Internally you can think of this:

// nums is passed in by reference. (i.e., without making a copy)
int len = removeDuplicates(nums);

// any modification to nums in your function would be known by the caller.
// using the length returned by your function, it prints the first len elements.
for (int i = 0; i < len; i++) {
    print(nums[i]);
}
## 问题分析
重复次数不超过2次即可
## 解题思路
只需要维护一个counter，当counter是2时，就直接跳过即可，否则说明元素出现次数没有超，继续放入结果数组，若遇到新元素则重置counter。总体算法只需要扫描一次数组，所以时间上是O(n)，空间上只需要维护一个index和counter，所以是O(1)
## 代码实现
```C++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
    int idx = 0;
    int count = 0;
    for(int i=0;i<nums.size();i++)
    {
        if(i>0 && nums[i]==nums[i-1])
        {
            count++;
            if(count>=3)
                continue;
        }
        else
        {
            count = 1;
        }
        nums[idx++]=nums[i];
    }
    return idx;
    }
};
```
