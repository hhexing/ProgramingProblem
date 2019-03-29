## Fibonacci

## 题目描述

Fibonacci数列是这样定义的：
F[0] = 0
F[1] = 1
for each i ≥ 2: F[i] = F[i-1] + F[i-2]
因此，Fibonacci数列就形如：0, 1, 1, 2, 3, 5, 8, 13, ...，在Fibonacci数列中的数我们称为Fibonacci数。给你一个N，你想让其变为一个Fibonacci数，每一步你可以把当前数字X变为X-1或者X+1，现在给你一个数N求最少需要多少步可以变为Fibonacci数。

## 输入描述:

```
输入为一个正整数N(1 ≤ N ≤ 1,000,000)
```

## 输出描述:

```
输出一个最小的步数变为Fibonacci数"
```

示例1

## 输入

复制

```
15
```

## 输出

复制

```
2
```

```
#include <iostream>
using namespace std;

int main()
{
    int n;
    cin >> n;
    int n1 = 0;
    int n2 = 1;
    int n3 = 1;
    while(n3 < n)
    {
        n3 = n1 + n2;
        n1 = n2;
        n2 = n3;
    }
    int left = n - n1;
    int right = n2 - n;
    if(left < right)
        cout << left << endl;
    else
        cout << right << endl;
    return 0;
}
```

## 合法括号序列判断

## 题目描述

对于一个字符串，请设计一个算法，判断其是否为一个合法的括号串。

给定一个字符串**A**和它的长度**n**，请返回一个bool值代表它是否为一个合法的括号串。

测试样例：

```
"(()())",6
返回：true
```

测试样例：

```
"()a()()",7
返回：false
```

测试样例：

```
"()(()()",7
返回：false
```

代码：

```
class Parenthesis {
public:
    bool chkParenthesis(string A, int n) {
        // write code here
        stack<char> sc;
        for(int i = 0; i < n; i++)
        {
            if(A[i] != '(' && A[i] != ')')
                return false;
            if(A[i] == '(')
                sc.push(A[i]);
            else if(A[i] == ')')
            {
                if(sc.empty() || sc.top() != '(')
                    return false;
                else
                    sc.pop();
            }
        }
        if(sc.empty())
            return true;
        else
            return false;
    }
};

```

代码：

```
class Parenthesis {
public:
    bool chkParenthesis(string A, int n) {
        // write code here
        stack<char> sc;
        for(auto e: A)
        {
            switch(e)
            {
                case '(':
                    sc.push(e);
                    break;
                case ')':
                    if(sc.empty() || sc.top() != '(')
                        return false;
                    else
                        sc.pop();
                    break;
                default:
                    return false;
            }
        }
        if(sc.empty())
            return true;
        else
            return false;
    }
};
```

