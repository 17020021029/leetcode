# 回文数字

## update

   今天看到大家的算法，觉得之前把int转为char的解法实在太麻烦了，赶紧又自己写了个，发现这样写简直简单到炸裂啊~~~
   
## 代码

```
bool isPalindrome(int x) {
    if(x<0)
        return false;
    else{
    int num_x;
    num_x=x;
    int result=0;
    while(num_x>0)
    {
        result=result*10+num_x%10;
        num_x=num_x/10;
    }
    if(result==x)
        return true;
    else return false;
    }
}
```
### 反思

尽管算法写起来简单，但我没想出来啊，妈耶，还有，中间没有注意数字小于0的情况，wrong了一次
