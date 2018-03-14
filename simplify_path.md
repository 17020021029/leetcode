# Simplify Path
## Problem 
Given an absolute path for a file (Unix-style), simplify it.

For example,
path = "/home/", => "/home"
path = "/a/./b/../../c/", => "/c"

click to show corner cases.
Corner Cases:

    Did you consider the case where path = "/../"?
    In this case, you should return "/".
    Another corner case is the path might contain multiple slashes '/' together, such as "/home//foo/".
    In this case, you should ignore redundant slashes and return "/home/foo".
## 问题分析
主要是对数组遍历分情况对数组inking处理，
## 代码实现
```C
char* simplifyPath(char* path) {
    int i, t=1;//i用做数组下标，t用来计算返回路径的下标
	int len = strlen(path);
	path[0] = '/';  //返回的路径第一个都为'/'
    for(i=1; i<len; i++) {
        if(path[i]=='.' && ((i+1<len && path[i+1]=='/') || path[i+1]=='\0')) {
            i = i + 1;
        } 
        else if(path[i]=='.' && i+1<len && path[i+1]=='.' && ((i+2<len && path[i+2]=='/') || path[i+2]=='\0')) {
            i = i + 2;
            t = t - 2 < 0? 0: t-2;
            while(path[t]!='/') {
                t--;
            }
			t++;
        } 
        else if(path[i]=='/') {
			continue;
		} 
    else {
            while(i<len && path[i]!='/'){
                path[t++] = path[i++];
            } 
            path[t++] = path[i];
        }
    }
	if(t>1) {
		path[t-1] = '\0';
	} 
    else {
		path[t] = '\0';
	}
	return path;
}

```
