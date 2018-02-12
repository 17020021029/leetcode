# Single Number
异或运算
## Problem
Given an array of integers, every element appears twice except for one. Find that single one.</br>
Note:
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory? 
## 解题过程
第一反应这道题应该是简单的通过遍历过程对数组的处理，但若是通过这种方法写出来的，想了很多种解法，都要经过好几次遍历，时间复杂度很高，不符合note的要求</br>
### Approach1
我的第一种方法是两层遍历，找是否有与第一层数相同的，若不相同，则返回,但是会出现，还没遍历完直接返回的情况，显然不对，那要从对立面算，那可以在外层循环加一个count，若外层数组找到与其相同的元素，则将count变为1；在外层循环中，若此时的count为0，则返回该层的元素</br>
但是不能实现，三个元素既不能返回正确结果
代码
```
int singleNumber(int* nums, int numsSize) {
    int count=0;
    int result=0;
    for(int i=0;i<numsSize;i++){
        for(int j=0;j<numsSize;j++)
        {
            if((*(nums+i)==*(nums+j))&&(i!=j))
                count=1;
        }
        if(count==0){
            result=i;}
    }
    return nums[result];
}
```
### Approach2
答案是python的解法，最终得出结论是用异或运算解这道题最好,其中的数学方法用python写起来简单，但用c好像不时间复杂度不满足</br>
异或运算（c++/c中运算符为"^"）的规则：a^b = (¬a ∧ b) ∨ (a ∧¬b)</br>
1. a^a=0
2. a^b=b^a
3. a^b^c=a^(b^c)=(a^b)^c
4. d=a^b^c=>a=d^b^c
5. a^b^a=b
6. 若x是二进制数0101，y是二进制数1011=>x^y=1110(只有在两个比较的位不同时其结果是1，否则结果为0
即“两个输入相同时为0，不同则为1”！)
代码实现
```ruby
int singleNumber(int* nums, int numsSize) {
    int s=0;
    for(int i=0;i<numsSize;i++)
    {
        s=s^nums[i];
    }
    return s;
}
```
## 总结
异或运算的应用


