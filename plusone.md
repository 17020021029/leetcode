# Plus One
整型数组
## Problem
Given a non-negative integer represented as a non-empty array of digits, plus one to the integer.</br>
You may assume the integer do not contain any leading zero, except the number 0 itself.</br>
The digits are stored such that the most significant digit is at the head of the list.
## 分析
将整型数组看作一个整数，然后进行加一运算，即对数组的处理实现对整数的加一运算</br>
解题的关键在于是否进位，若进位，要重新申请digitsSize+1个元素的整型数组
## 解题过程
### 一
思路：申请一个新的数组用作返回值，申请两个整型，一个作为进位的值，一个作为当前的数组元素值，分别计算，若最后的进位值为1，则要重新申请数组，否则直接输出运算的数组</br>

#### 代码实现*BUT：Compile Error*
```ruby
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* plusOne(int* digits, int digitsSize, int* returnSize) {
    int *result;
    int i,carry=1,num;    /*carry为进位，num为留位*/
    for(i=digitsSize-1;i>=0;i++)
    {
        num=(*(digits+i)+carry)%10;
        carry=(*(digits+i)+carry)/10;
        *(digits+i)=num;
    }
    if(num==1)
    {
        *result=malloc(sizeof(int)*(digitsSize+1));
        *(result+i)=0;
        for(i=0;i<digitsSize+1;i++)
            *(result+i+1)=*(digits+i);
        *returnSize=digitsSize+1;
        return result;
    }
    else
    {
        *returnSize=digitsSize;
        return digits;
    }
}
```
### 二
经学长教导，（打字的手真真的在颤抖），恍然大悟，竟然是因为那么多小错误导致出错，不知道怎么说好（该打该打），一直没改掉的毛病我就不信改不了！！！
#### 正确代码
```ruby
/**
 * Return an array of size *returnSize.
 * Note: The returned array must be malloced, assume caller calls free().
 */
int* plusOne(int* digits, int digitsSize, int* returnSize) {
    int *result;
    int i,carry=1,num;    /*carry为进位，num为留位*/
    for(i=digitsSize-1;i>=0;i--)        //误将i--写为i++
    {
        num=(*(digits+i)+carry)%10;
        carry=(*(digits+i)+carry)/10;
        *(digits+i)=num;
    }
    if(carry==1)       // 明明怕忘了在前边注明了那个是留位，那个是进位，可还是写错
    {
        result=(int*)malloc(sizeof(int)*(digitsSize+1));        //malloc的用法，多加了个*
        *(result)=1;
        for(i=0;i<digitsSize;i++)   
            *(result+i+1)=*(digits+i);
        *returnSize=digitsSize+1;
        return result;
    }
    else
    {
        *returnSize=digitsSize;
        return digits;
    }
}
```
