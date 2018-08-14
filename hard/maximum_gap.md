## Problem
给定一个无序的数组，找出数组在排序之后，相邻元素之间最大的差值。

如果数组元素个数小于 2，则返回 0。

示例 1:

输入: [3,6,9,1]
输出: 3
解释: 排序后的数组是 [1,3,6,9], 其中相邻元素 (3,6) 和 (6,9) 之间都存在最大差值 3。

示例 2:

输入: [10]
输出: 0
解释: 数组元素个数小于 2，因此返回 0。
## 解题思路
开始想到的最简单的方法是排序后遍历，但是代码一直有问题
```
class Solution {
public:
    int maximumGap(vector<int>& nums) {
        if(nums.size()<2)
            return 0;
        int res=0;
        sort(nums.begin(),nums.end());
        for(int i=0;i<nums.size();i++){
            int temp=0;
            temp=nums[i+1]-nums[i];
            if(temp>res)
                res=temp;
        }
        return res;
    }
};
```
参考的代码，但是由于知识局限，写不出来这样的代码
```C++
inline int maxNum(int a, int b){return (a>b)?a:b;}
 
class Solution {
public:
    int maximumGap(vector<int>& nums) {
        if(nums.size()<2)
            return 0;
        
        set<int> mapNums;
        for(int i=0;i<nums.size();++i)
            mapNums.insert(nums[i]);
        
        int max=0;
        set<int>::iterator it=mapNums.begin();
        set<int>::iterator it2=it;
        it2++;
        
        while(it2!=mapNums.end()){
            max=maxNum(max, *it2-*it);
            it++;
            it2++;
        }
 
        return max;
    }
};
```
