# c++ 常用代码合集
## 高级c++头文件
```language
#include<bits/stdc++.h>
using namespace std;
```
## STL模板
STL容器分为多种，如序列容器，排序容器，哈希容器。
- 序列容器：vector， list， deque
- 排序容器：set，map， multiset（多重集合容器），multimap（多重映射容器）
- 哈希容器：unordered_set 哈希集合、unordered_multiset 哈希多重集合、unordered_map 哈希映射以及 unordered_multimap 哈希多重映射

## vector常用语法
- 容器特性：顺序，xx
- 增加函数
```language
//尾部添加
res.push_back(x)
//添加指定位置元素
res.insert(res.begin() + 1, 3)
//比insert效率更高
res.emplace(demo1.begin(), 3);
```
- 删除函数
```language
//尾部删除
res.pop_back()
//删除指定位置元素
res.erase(demo.begin() + 1)
```
- 数组排序
```language
//默认从小到大
sort(piles.begin(), piles.end(),less<int>());
//从大到小
sort(piles.begin(), piles.end(),greater<int>());
//自定义

```
- 数组初始化&赋值
```language
vector<vector<int> > obj(N, vector<int>(M))
```
## set常用用法
set特性：底层实现红黑树
- 元素数量查询
```language
res.count(x)
```
- 查找是否有元素
```language
s.find(x)) != s.end()
```
## unordered_set常用语法
- unordered_set特性：底层哈希

## map常用语法
```language
map<int, string> mapStudent;  
//插入元素
mapStudent.insert(pair<int, string>(1, "student_one"));
//插入元素2，与第一种的区别是重复键值会覆盖。
mapStudent[1] = "student_one";
```
## priority_queue常用语法
priority_queue <int,vector<int>,greater<int> > q;
```language
q.push(k);//在q的末尾插入k
q.pop();//删掉q的第一个元素
q.top();//返回q的第一个元素
```





