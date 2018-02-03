#题目描述  
Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

 Note:
You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2. The number of elements initialized in nums1 and nums2 are m and n respectively.
  *开始没弄明白note的意思，重新申请了一个动态数组，结果在当m或n为0时溢出
  
##解题过程

###一：
没有理解note的意思，重新申请动态数组，结果忽略了数组长度为0的情况

```
void merge(int* nums1, int m, int* nums2, int n) {
    int *str;
    str=(int *)malloc(sizeof(int)*(m+n));
    for(int i=0;i<m;i++)
    {
        *(str+i)=*(nums1+i);
    }
    int i=0;
    for(int j=m;j<m+n&&i<n;j++)
    {
    
        *(str+j)=*(nums2+i);
        i++;
    }
    for(int i=0;i<m+n-1;i++)
    {
        for(int j=0;j<m+n-1-i;j++)
        {
            int temp;
            temp=str[i];
            str[i]=str[i+1];
            str[i+1]=temp;
        }
    }
    return str;
}
```

###二、
将nums1看做足够的的数组，那只要比较nums1和nums2的大小，再赋值给nums1即可，关键是逆向遍历，就可以避免上面的问题,然后一遍过了，贼开心，
不过，这个算法的时间复杂度好像emmmmmm

```
void merge(int* nums1, int m, int* nums2, int n) {
    while(m>0&&n>0)
    {
        if(*(nums1+m-1)>*(nums2+n-1))
           {
               *(nums1+m+n-1)=*(nums1+m-1);
               m--;
           }
           else
           {
               *(nums1+m+n-1)=*(nums2+n-1);
               n--;
           }
    }
    while(m>0)
    {
        *(nums1+m+n-1)=*(nums1+m-1);
        m--;
    }
    while(n>0)
    {
        *(nums1+m+n-1)=*(nums2+n-1);
        n--;
    }
    return nums1;
}
```
##反思：
之前习惯正向的遍历，没太有逆向遍历的意识，第二种方法理解起来倒是不难，但是时间复杂度上还是不太理想，emmmm

