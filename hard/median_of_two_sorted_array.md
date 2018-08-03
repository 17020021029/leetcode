## Problem
给定两个大小为 m 和 n 的有序数组 nums1 和 nums2 。

请找出这两个有序数组的中位数。要求算法的时间复杂度为 O(log (m+n)) 。

你可以假设 nums1 和 nums2 均不为空。

 

示例 1:

nums1 = [1, 3]
nums2 = [2]

中位数是 2.0
示例 2:

nums1 = [1, 2]
nums2 = [3, 4]

中位数是 (2 + 3)/2 = 2.5
## 解题思路
就是最暴力的解法，将两个数组合并，分奇偶返回中位数
## 代码实现
```C++
class Solution {
public:
    double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
        int size1=nums1.size();
        int size2=nums2.size();
        vector<int> nums;
        int s1=0,s2=0;
        while(s1<size1&&s2<size2){
            if(nums1[s1]<nums2[s2]){
                nums.push_back(nums1[s1]);
                s1++;
            }
            else{
                nums.push_back(nums2[s2]);
                s2++;
            }
        }
        while(s1<size1){
            nums.push_back(nums1[s1]);
            s1++;
        }
        while(s2<size2){
            nums.push_back(nums2[s2]);
            s2++;
        }
        
        if((size1+size2)%2==0)
            return (nums[(s1+s2)/2]+nums[(s1+s2)/2-1])/2.0;
        return nums[(s1+s2)/2];
    }
};
```
