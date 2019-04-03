# 最近公共祖先

## 题目描述

有一棵无穷大的满二叉树，其结点按根结点一层一层地从左往右依次编号，根结点编号为1。现在有两个结点a，b。请设计一个算法，求出a和b点的最近公共祖先的编号。

给定两个int **a**,**b**。为给定结点的编号。请返回**a**和**b**的最近公共祖先的编号。注意这里结点本身也可认为是其祖先。

测试样例：

```c++
2，3
返回：1
```

https://www.nowcoder.com/practice/70e00e490b454006976c1fdf47f155d9?tpId=8&&tqId=11017&rp=1&ru=/activity/oj&qru=/ta/cracking-the-coding-interview/question-ranking

代码（循环的思想，每次都是大的/2)：

```
class LCA {
public:
    int getLCA(int a, int b) {
       while( a != b)
       {
           if(a > b)
               a /= 2;
           else
               b /= 2;
       }
       return a;
    }
};
```

# 最大连续bit位

## 题目描述

功能: 求一个byte数字对应的二进制数字中1的最大连续数，例如3的二进制为00000011，最大连续2个1
    
输入: 一个byte型的数字
    
输出: 无
     
返回: 对应的二进制数字中1的最大连续数

## 输入描述:

```
输入一个byte数字
```

## 输出描述:

```
输出转成二进制之后连续1的个数
```

示例1

## 输入

复制

```
3
```

## 输出

复制

```
2
```

https://www.nowcoder.com/practice/4b1658fd8ffb4217bc3b7e85a38cfaf2?tpId=37&&tqId=21309&rp=1&ru=/activity/oj&qru=/ta/huawei/question-ranking

代码：

```
#include <iostream>
using namespace std;

int main()
{
    int byte;
    while(cin >> byte)
    {
        int max = 0;
        int cur = 0;
        while(byte != 0)
        {
            if(byte%2 ==1)
            {
                cur++;
                if(cur > max)
                    max = cur;
            }
            else
                cur = 0;
            byte /= 2;
        }
        cout << max << endl;
    }
    return 0;
}
```

