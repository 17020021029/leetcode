# Integer to Roman
 代码看上去更简单
## 思路
今天复习这道题的时候，猛然再[百度百科](https://baike.baidu.com/item/%E7%BD%97%E9%A9%AC%E6%95%B0%E5%AD%97/772296?fr=aladdin#8)上看到这道题的算法，而且是1到3999，看来这道题是一道很经典的题了

这道题的整体思路是和昨天的大致相同，都是考虑到整型的大小对字母的影响，但这个是直接把整数分离，各部分直接转换成字符串再连接，涉及到[append函数](https://zhidao.baidu.com/question/1735165904946516547.html?qbl=relate_question_0&word=append%28%29c%2B%2B),都是C++中string类的用法

## 代码实现
```
class Solution {
public:
    string intToRoman(int num) {
        char* c[4][10]={
            {"","I","II","III","IV","V","VI","VII","VIII","IX"},
            {"","X","XX","XXX","XL","L","LX","LXX","LXXX","XC"},
            {"","C","CC","CCC","CD","D","DC","DCC","DCCC","CM"},
            {"","M","MM","MMM"}
        };
        string roman;
        roman.append(c[3][num / 1000 % 10]);   //append()将括号内的字符串加到或连接到roman字符串
        roman.append(c[2][num / 100 % 10]);
        roman.append(c[1][num / 10 % 10]);
        roman.append(c[0][num % 10]);
         
        return roman;
    }
};
```
## 反思
这个写法很巧妙的一点是把各位数的大小作为了数组的下标，也正是因为给定的整型大小很小，也才给了这种算法实现的条件
