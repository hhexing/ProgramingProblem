# 字符串中找到连续最长的数字串

## 题目描述

读入一个字符串str，输出字符串str中的连续最长的数字串

## 输入描述:

```
个测试输入包含1个测试用例，一个字符串str，长度不超过255。
```

## 输出描述:

```
在一行内输出str中里连续最长的数字串。
```

示例1

## 输入

复制

```
abcd12345ed125ss123456789
```

## 输出

复制

```
123456789
```

<https://www.nowcoder.com/practice/bd891093881d4ddf9e56e7cc8416562d?tpId=85&&tqId=29864&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking>

代码：**和找出最大连续子序列和思路一样，这个多一个用str保存数字串**

```
#include <string>
#include <iostream>
using namespace std;

int main()
{
    string str, cur, ret;
    cin >> str;
    for(int i = 0; i <= str.size(); i++)
    {
        if(isdigit(str[i]))
            cur += str[i];
        else
        {
            if(cur.size() > ret.size())
                ret = cur;
            cur = "";
        }
    }
    cout << ret << endl;
    return 0;
}
```

# n个数里出现次数大于n/2的数

## 题目描述

输入n个整数，输出出现次数大于等于数组长度一半的数。

## 输入描述:

```
每个测试输入包含 n个空格分割的n个整数，n不超过100，其中有一个整数出现次数大于等于n/2。
```

## 输出描述:

```
输出出现次数大于等于n/2的数。
```

示例1

## 输入

复制

```
3 9 3 2 5 6 7 3 2 3 3 3
```

## 输出

复制

```
3
```

<https://www.nowcoder.com/practice/eac8c671a0c345b38aa0c07aba40097b?tpId=85&&tqId=29866&rp=1&ru=/activity/oj&qru=/ta/2017test/question-ranking>

代码：**推荐使用，简单，排序之后，中间出现的那个元素**

```
#include <algorithm>
#include <iostream>
using namespace std;

int main()
{
    int n;
    vector<int> vec;
    while(cin >> n)
        vec.push_back(n);
    int count = 1;
    int tmp = vec[0];
    sort(vec.begin(), vec.end());
    int mid = vec.size()/2 -1;
    cout << vec[mid] << endl;
    return 0;
}
```

代码：**抵消的思想**

```
#include <algorithm>
#include <iostream>
using namespace std;

int main()
{
    int n;
    vector<int> vec;
    while(cin >> n)
        vec.push_back(n);
    int count = 1;
    int tmp = vec[0];
    for(int i = 1; i < vec.size(); i++)
    {
        if(tmp == vec[i])
            count++;
        else
            count--;
        if(count == 0)
        {
            tmp = vec[i];
            count++;
        }
    }
    cout << tmp << endl;
    return 0;
}
```

