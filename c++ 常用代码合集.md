# c++ 常用代码合集
## 高级c++头文件
```language
#include<bits/stdc++.h>
using namespace std;
ios::sync_with_stdio(false);//关掉scanf和cin的同步，提升效率
while(scanf("%d%d",&n,&m)!=EOF)
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
priority_queue <int,vector<int>,less<int> >q;//从大到小
priority_queue <int,vector<int>,greater<int> > q;//从小到大
priority_queue< pair<int, int> > q2; // 注意在两个尖括号之间一定要留空格。
```language
q.push(k);//在q的末尾插入k
q.pop();//删掉q的第一个元素
q.top();//返回q的第一个元素
```
## queue && deque常用用法
```language
queue<int> q;
q.push(x)
q.pop();
//队头元素
q.front();
//队尾元素
q.back();
```
deque是双端队列
```language
deque<int> dq;
dq.push_front(x);
dq.push_back(x);
dq.pop_front();
dq.pop_back();
```
## stack语法
stack、queue，priority_queue是适配器，因为是对容器的再封装
```language
s.push(x)
s.pop()
s.top()
```
## string语法
//复制，也可直接赋值
strcpy( str3, str1);
//连接，可
strcat( str1, str2);
//比较
strcmp(s1, s2);

//str1的第6个字符以及后面的4个字符和str2的第4个字符以及后面的4个字符比较
if (str1.compare(6,5,str2,4,5) == 0)
//返回一个指针，指向字符串第一次出现ch的位置
strchr(s1, ch);
//返回一个指针，指向字符串第一次出现s2的位
strstr(s1, s2);
```language
string s="abcdefg";
//s.substr(pos1,n)返回字符串位置为pos1后面的n个字符组成的串
string s2=s.substr(1,5);//bcdef
//s.substr(pos)//得到一个pos到结尾的串
string s3=s.substr(4);//efg

//s.insert(pos,str)//在s的pos位置插入str
str.insert(6,str2); 

str.erase (10,8);       //            ^^^^^^^^
//直接指定删除的字符串位置第十个后面的8个字符
std::cout << str << '\n';
                            // "This is an sentence."
str.erase (str.begin()+9);//           ^
//删除迭代器指向的字符
std::cout << str << '\n';
                            // "This is a sentence."
                            //       ^^^^^
str.erase (str.begin()+5, str.end()-9);
//删除迭代器范围的字符

//第9个字符以及后面的4个字符被str2代替
str.replace(9,5,str2); 
//迭代器
str.replace(str.begin(),str.end()-3,str3);  

//直接把base赋值给str
str.assign(base);
std::size_t found = str.find(str2);
if (found!=std::string::npos)
std::cout << "first 'needle' found at: " << found << '\n';
//在str当中，从第found+1的位置开始查找参数字符串的前6个字符
found=str.find("needles are small",found+1,6);
//rfind从后往前找

find_first_of(args) 查找args中任何一个字符第一次出现的位置
find_last_of(args) 最后一个出现的位置
find_fist_not_of(args) 查找第一个不在args中的字符
find_last_not_of 查找最后一个不在args中出现的字符
```

## 重载运算符示例
```language
看下面这个简单的示例：
#include <iostream>

#include <queue>
using namespace std;
class T
{
public:
int x, y, z;
T(int a, int b, int c):x(a), y(b), z(c)
{
}
};
bool operator < (const T &t1, const T &t2)
{
return t1.z < t2.z; // 按照z 的顺序来决定t1 和t2 的顺序
}
main()
{
priority_queue<T> q;
q.push(T(4,4,3));
q.push(T(2,2,5));
q.push(T(1,5,4));
q.push(T(3,3,6));
while (!q.empty())
{
T t = q.top(); q.pop();
cout << t.x << " " << t.y << " " << t.z << endl;
}
return 1;
}
输出结果为(注意是按照z 的顺序从大到小出队的)：
3 3 6
2 2 5
1 5 4
4 4 3
再看一个按照z 的顺序从小到大出队的例子：
#include <iostream>
#include <queue>
using namespace std;
class T
{
public:
int x, y, z;
T(int a, int b, int c):x(a), y(b), z(c)
{
}
};
bool operator > (const T &t1, const T &t2)
{
return t1.z > t2.z;
}
main()
{
priority_queue<T, vector<T>, greater<T> > q;
q.push(T(4,4,3));
q.push(T(2,2,5));
q.push(T(1,5,4));
q.push(T(3,3,6));
while (!q.empty())
{
T t = q.top(); q.pop();
cout << t.x << " " << t.y << " " << t.z << endl;
}
return 1;
}
```
## 元素类型转换
|string和数值转换|column2|
|-|-|
|to_string(val)|把val转换成string|
|stoi(s)|把string转换成int|
|atoi(s)|把char转换成int|
```language
// char[]转换为string 
char st[] = "hello";   
// 直接赋值实现 
string st1 = st

应该这样用： 
char c[20]; 
string s="1234"; 
strcpy(c,s.c_str()); 
这样才不会出错，c_str()返回的是一个临时指针，不能对其进行操作
 
再举个例子
c_str() 以 char* 形式传回 string 内含字符串
如果一个函数要求char*参数，可以使用c_str()方法： 
string s = "Hello World!";
printf("%s", s.c_str()); //输出 "Hello World!"
```

## 定义数值

## 链表结构

## 树结构

## 并查集代码





