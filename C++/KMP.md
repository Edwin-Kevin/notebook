# KMP 算法

## 算法概述

用`pat`表示模式串，长度为`M`，`txt`表示文本串，长度为`N`。`KMP`算法是在`txt`中查找子串`pat`，如果存在，返回这个子串的起始索引，否则返回`-1`。

KMP 算法永不回退`txt`的指针`i`，不走回头路（不会重复扫描`txt`），而是借助`dp`数组中储存的信息把`pat`移到正确的位置继续匹配，时间复杂度只需 O(N)，用空间换时间，是一种动态规划算法。

KMP 算法的难点在于，如何计算`dp`数组中的信息？如何根据这些信息正确地移动`pat`的指针？

计算这个`dp`数组，只和`pat`串有关。

## 状态机

为了描述状态转移图，定义一个二维 dp 数组，它的含义如下：
```
dp[j][c] = next
0 <= j < M，代表当前的状态
0 <= c < 256，代表遇到的字符（ASCII 码）
0 <= next <= M，代表下一个状态

dp[4]['A'] = 3 表示：
当前是状态 4，如果遇到字符 A，
pat 应该转移到状态 3

dp[1]['B'] = 2 表示：
当前是状态 1，如果遇到字符 B，
pat 应该转移到状态 2
```

## 构建状态转移图

要确定状态转移的行为，必须明确两个变量，一个是当前的匹配状态，另一个是遇到的字符。

构造`dp`数组的框架：
```
for 0 <= j < M: # 状态
    for 0 <= c < 256: # 字符
        dp[j][c] = next
```

如果遇到的字符`c`和`pat[j]`匹配的话，状态就应该向前推进一个，也就是说`next = j + 1`，我们不妨称这种情况为**状态推进**。

如果遇到的字符`c`和`pat[j]`不匹配的话，状态就要回退（或者原地不动），我们不妨称这种情况为**状态重启**。

## 代码实现（28）
```
class Solution {
public:
    void getNext(int* next, const string &s){
        int j = -1;
        next[0] = -1;
        for(int i = 1; i < s.size(); i++){
            while(j >= 0 && s[i] != s[j + 1]){
                j = next[j];
            }
            if(s[i] == s[j + 1]){
                j++;
            }
            next[i] = j;
        }
    }
    int strStr(string haystack, string needle) {
        if(needle.size() == 0)  return 0;
        vector<int> next(needle.size());
        getNext(&next[0], needle);
        int j = -1;
        for(int i = 0; i < haystack.size(); i++){
            while(j >= 0 && haystack[i] != needle[j + 1]){
                j = next[j];
            }
            if(haystack[i] == needle[j + 1]){
                j++;
            }
            if(j == (needle.size() - 1)){
                return (i - needle.size() + 1);
            }
        }
        return -1;
    }
};
```