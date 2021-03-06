# 只出现一次的数字
给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素
requests:线性时间复杂度、不需要新的空间
## 代码
```
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        int num=0;
        int i=0;
        for (i=0;i<nums.size();i++){
            num = num^nums[i];
        }
        return num;
        }
};
```
## 方法
异或的用法
因为题目中已说明重复的元素均出现两次，可以利用异或运算的性质，相同的数结果为0，与0异或的数为原来的数，对数组进行遍历
