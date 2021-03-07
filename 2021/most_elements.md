# 多数元素
给定一个大小为 n 的数组，找到其中的多数元素。多数元素是指在数组中出现次数 大于 ⌊ n/2 ⌋ 的元素。

你可以假设数组是非空的，并且给定的数组总是存在多数元素。

## 代码
```
class Solution{
public:
int majorityelement(vector<int>& nums){
sort(nums.begin(),nums.end());
return nums[nums.size()/2];
}
};
```
## 运行结果
![image](https://user-images.githubusercontent.com/33409986/110241822-e68c4200-7f8d-11eb-95c9-e18f9bd614fb.png)
## 方法
看到底下的思路，本来我还想慢慢计数呢~~~

主要的困境是忘记了vector标准库的用法，查了好多书和网页才找到正确的用法

要好好回顾一下了
