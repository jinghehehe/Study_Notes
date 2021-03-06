# c++ 常用代码合集
Tools -> Complier Options -> Settings -> Code Generation -> Language Standard(-std) -> ISO c++11
## 高级c++头文件
```language
#include<bits/stdc++.h>
using namespace std;
ios::sync_with_stdio(false);//关掉scanf和cin的同步，提升效率
while(scanf("%d%d",&n,&m)!=EOF)
const int mod = 1e9 + 7;
(a∗b)%c=((a%c)∗(b%c))%c
map<int, unordered_map<int, array<vector<int>, 2>>> actions
```
## STL模板
STL容器分为多种，如序列容器，排序容器，哈希容器。
- 序列容器：vector， list， deque
- 排序容器：set，map， multiset（多重集合容器），multimap（多重映射容器）
- 哈希容器：unordered_set 哈希集合、unordered_multiset 哈希多重集合、unordered_map 哈希映射以及 unordered_multimap 哈希多重映射

## vector常用语法
- 容器特性：顺序，xx
- //反转
- reverse(str.begin(),str.end());
- 增加函数
```language
//尾部添加
res.push_back(x)
//添加指定位置元素
res.insert(res.begin() + 1, 3)
//比insert效率更高
res.emplace(demo1.begin(), 3);
//数组拷贝
result.assign(res.begin(),res.begin()+depth);
result.assign(n,num);
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
pos = find_if(intVec.begin(),intVec.end(),
		not1(bind2nd(modulus<int>(),3)));

printf("%02X",n)：将10进制数n输出成16进制数，其中10~15用大写字母A~F表示，输出的16进制数不足两位在高位补0
stoi(s,0,16)：将16进制字符串s转换成10进制数并返回
```
## list用法
```language
push_back() 和push_front()
pop_back和pop_front()，但元素不能为空
assign()：具体和vector中的操作类似，也是有两种情况，第一种是：l1.assign(n,val)将 l1中元素变为n个T(val）。第二种情况是：l1.assign(l2.begin(),l2.end())将l2中的从l2.begin()到l2.end()之间的数值赋值给l1。

reverse
merge()：合并两个链表并使之默认升序(也可改)，l1.merge(l2，greater<int>()); 调用结束后l2变为空，l1中元素包含原来l1 和 l2中的元素，并且排好序，升序。其实默认是升序，greater<int>()可以省略，另外greater<int>()是可以变的，也可以不按升序排列。

1.insert(l1.begin(),100); 在l1的开始位置插入100。

l1.insert(l1.begin(),2,200); 在l1的开始位置插入2个100。

l1.insert(l1.begin(),l2.begin(),l2.end());在l1的开始位置插入l2的从开始到结束的所有位置的元素。
l1.erase(l1.begin()); 将l1的第一个元素删除。

l1.erase(l1.begin(),l1.end()); 将l1的从begin()到end()之间的元素删除。
```
## array用法
```language
array<double,100> data
values.fill(3.1415926);
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

## 排序
```language
// Ascending order by second column
sort(m.begin(), m.end(), [](const vector<int> &a, const vector<int> &b) { return a[1] < b[1]; } );

bool cmp(const vector<int> &a, const vector<int> &b) {
    return a[0] > b[0];
}
sort(m.begin(), m.end(), cmp);
```


## 链表结构
```language
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* createList(int n,vector<int> res)
	{
		ListNode* phead=new ListNode(res[0]);
        ListNode* head = phead; //不破坏头指针
		for(int i=1;i<n;i++){
			phead->next=new ListNode(res[i]);

			phead=phead->next;
		}
        return head;
	}
    ListNode* sortList(ListNode* head) {
        vector<int> res;
        if(head == NULL) return NULL;
        while(head!=NULL){
            res.push_back(head->val);
            head = head->next;
           // cout << res.back();
        }
        sort(res.begin(),res.end());
        int len = res.size();
        ListNode* phead = createList(len,res);
        return phead;
    }
};

class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode* cur = NULL, *pre = head;
        while (pre != NULL) {
            ListNode* t = pre->next;
            pre->next = cur;
            cur = pre;
            pre = t;
        }
        return cur;
    }
};

鲁棒性1: 如果链表为空。如果代码试图访问空指针指向的内存，程序就会崩溃，需要合理处理。
鲁棒性2: 如果 k = 0。因为 k 是无符号整数，在 for 循环中 k - 1 不是 -1，而是一个超级大的数，会循环很多次，也会使程序崩溃。
鲁棒性3: 链表的节点总数小于 k。由于 for 循环中需要走 k - 1 步，也有可能由于空指针而造成程序崩溃。


/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* getKthFromEnd(ListNode* head, int k) {
        if(!head || k == 0) return nullptr; // 鲁棒性1、2
        ListNode *fast = head, *slow = head;
        for(int i=1; i<=k-1; ++i)
        {
            if(fast -> next) fast = fast -> next; // 鲁棒性3
            else return nullptr;
        }
        while(fast -> next)
        {
            fast = fast -> next;
            slow = slow -> next;
        }
        return slow;
    }
};


```

## 树结构
```language
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    vector<double> averageOfLevels(TreeNode* root) {
        queue<TreeNode*> que;
        if (root != NULL) que.push(root);
        vector<double> result;
        while (!que.empty()) {
            int size = que.size();
            double sum = 0; // 统计每一层的和
            for (int i = 0; i < size; i++) { // 这里一定要使用固定大小size，不要使用que.size()
                TreeNode* node = que.front();
                que.pop();
                sum += node->val;
                if (node->left) que.push(node->left);
                if (node->right) que.push(node->right);
            }
            result.push_back(sum / size); // 将每一层放进结果集
        }
        return result;
    }
};
//树的深度
int  GetBTreeDepth( BTreeNode_t *pRoot)
{
    if( pRoot == NULL )
        return 0;
 
    int lDepth = GetBTreeDepth( pRoot->m_pLeft);
    int rDepth = GetBTreeDepth( pRoot->m_pRight);
 
    return ((( lDepth > rDepth )? lDepth: rDepth) + 1 );        
}


```

## c++输入字符串（含空格）
- getline()
```language
string st;
getline(cin,st);
```
- cin.get，遇回车结束
```language
char st[50];
cin.get(st,50);
```
- cin.getline，getline将换行符丢弃，而get()将换行符保留在输入序列里
```language
char st[50];
cin.getline(a,50);
```

- 字符串类型转换为字符数组
```language
char p[50];
string str="I Love Ningbo!";
strcpy(p,str.c_str());
```
- 字符数组转换为字符串类型
```language
char ch [] = "ABCDEFG";
string str;
str = ch;//在原有基础上添加可以用str += ch;
```
- 特殊输入
```language
char st[50];
scanf("%[^\n]",st);// \n作为字符串输入的结束符
scanf("%[a-z A-Z0-9]",str); //表示只匹配输入是大小写字母和数字，遇到非数字和字母时输入结束。
```

- 输入

scanf 忽略行开头的所有空格，并以各种格式化进行数据输入，直到遇到 空格、回车 结束输入，不接收 空格 和 回车，留在缓存区中；
getchar 只读取一个字符，包括 空格 但是不包括 回车，回车 会留在缓冲区中；
gets 读取以任何字符开头的字符串，读取的字符串包括 空格 但是不包括 回车，以 回车 结束输入，接收 空格 和 回车，但之后会丢弃 回车 并以 \0 代替；
### gets前有scanf需要用scanf("\n");/gets();/getchar();来去除回车
![fnppx8pwrb.png](0)


- 清空数组
```language
memset(sBuff,0,sizeof(sBuff));
or
sBuff[0]='\0';
```

## C、C++ 中 |、||、&、&&、异或、~、！运算详解
&(按位与)、|(按位或)、^(按位异或)、~ (按位取反)。
其中，按位取反运算符是单目运算符，其余均为双目运算符。
位运算符的优先级从高到低，依次为~、&、^、|，
移位运算符的优先级低于算术运算符，高于关系运算符，它们的结合方向是自左至右。
   (1)左移运算符(<<)
    左移运算将一个位串信息向左移指定的位，右端空出的位用0补充。例如014<<2,结果为060,即48。
    左移时，空出的右端用0补充，左端移出的位的信息就被丢弃。在二进制数运算中，在信息没有因移动而丢失的情况下，每左移1位相当于乘2。如4 << 2，结果为16。
   (2)右移运算符(>>)
    右移运算将一个位串信息向右移指定的位，右端移出的位的信息被丢弃。例如12>>2,结果为3。与左移相反，对于小整数，每右移1位，相当于除以2。在右移时，需要注意符号位问题。对无符号数据，右移时，左端空出的位用0补充。对于带符号的数据，如果移位前符号位为0(正数)，则左端也是用0补充；如果移位前符号位为1(负数)，则左端用0或用1补充，取决于计算机系统。对于负数右移，称用0 补充的系统为“逻辑右移”，用1补充的系统为“算术右移”。以下代码能说明读者上机的系统所采用的右移方法：
     printf("%d\n\n\n", -2>>4);
若输出结果为-1，是采用算术右移；输出结果为一个大整数，则为逻辑右移。



## 并查集代码（java）
```language
class UF {
    // 连通分量个数
    private int count;
    // 存储一棵树
    private int[] parent;
    // 记录树的“重量”
    private int[] size;

    public UF(int n) {
        this.count = n;
        parent = new int[n];
        size = new int[n];
        for (int i = 0; i < n; i++) {
            parent[i] = i;
            size[i] = 1;
        }
    }

    public void union(int p, int q) {
        int rootP = find(p);
        int rootQ = find(q);
        if (rootP == rootQ)
            return;

        // 小树接到大树下面，较平衡
        if (size[rootP] > size[rootQ]) {
            parent[rootQ] = rootP;
            size[rootP] += size[rootQ];
        } else {
            parent[rootP] = rootQ;
            size[rootQ] += size[rootP];
        }
        count--;
    }

    public boolean connected(int p, int q) {
        int rootP = find(p);
        int rootQ = find(q);
        return rootP == rootQ;
    }

    private int find(int x) {
        while (parent[x] != x) {
            // 进行路径压缩
            parent[x] = parent[parent[x]];
            x = parent[x];
        }
        return x;
    }

    public int count() {
        return count;
    }
}
```
## 推荐系统例题
```#include <bits/stdc++.h>
using namespace std;
struct Commodity {  //商品类
    long long id, score;  //id和分数
    Commodity(long long i, long long s) : id(i), score(s) {}
    bool operator<(const Commodity& c) const {  //重载小于运算符
        return this->score != c.score ? this->score > c.score : this->id < c.id;
    }
};
int main() {
    const long long mul = (long long)(1e9);
    int m, n, id, score, op, t, c, k;
    cin >> m >> n;
    vector<int> K(m);  //存储每类商品被选中的最多件数
    set<Commodity> commodities;  //对所有商品进行排序
    unordered_map<long long, set<Commodity>::iterator> um;  //存储商品id和对应的set中的迭代器
    for (int i = 0; i < n; ++i) {
        cin >> id >> score;
        for (int j = 0; j < m; ++j) {
            long long a = j * mul + id;
            um[a] = commodities.insert(Commodity(a, score)).first;
        }
    }
    cin >> op;
    while (op--) {
        cin >> c;
        if (c == 1) {  //添加商品
            cin >> t >> id >> score;
            long long a = t * mul + id;
            um[a] = commodities.insert(Commodity(a, score)).first;
        } else if (c == 2) {  //删除商品
            cin >> t >> id;
            long long a = t * mul + id;
            commodities.erase(um[a]);
            um.erase(a);
        } else {
            vector<vector<int>> ans(m);
            cin >> k;
            for (int i = 0; i < m; ++i)
                cin >> K[i];
            for (auto& i : commodities) {  //遍历整个set
                t = i.id / mul;
                if (ans[t].size() < K[t]) {
                    ans[t].push_back(i.id % mul);
                    if (--k == 0)  //商品已选满k件，结束遍历
                        break;
                }
            }
            for (auto& i : ans)
                if (i.empty()) {  //没有选中的商品，输出-1
                    cout << "-1\n";
                } else {
                    sort(i.begin(), i.end());//从小到大排序
                    for (auto j : i)
                        cout << j << " ";
                    cout << "\n";
                }
        }
    }
    return 0;
}

```

区块链
```language

  
#include <bits/stdc++.h>
using namespace std;
vector<vector<int>> graph(505);  //存储节点的边关系
vector<vector<int>> ans(505, {0});  //存储每个节点的主链
int n, m, t, k;
map<int, unordered_map<int, array<vector<int>, 2>>> actions;  //存储接收链和产生块操作
bool canAccept(const vector<int>& Old, const vector<int>& New) {  //其他节点传递过来的新链New能否被接受
    return Old.size() != New.size() ? Old.size() < New.size() : Old.back() > New.back();
}
void diffuse(int v, int time) {  //将节点v的主链广播出去
    for (int i : graph[v]) {
        auto& chain = actions[time][i][0];
        if ((chain.empty() and canAccept(ans[i], ans[v])) or (not chain.empty() and canAccept(chain, ans[v])))
            chain = ans[v];
    }
}
void query(int a, int b) {  //查询a节点在b时刻的主链
    for (auto& action : actions) {  //遍历所有接收链和产生块操作
        int curTime = action.first;
        if (curTime > b)  //当前操作时刻>b，结束循环
            break;
        for (auto& vertex : action.second) {
            int v = vertex.first;  //获取该操作节点编号
            auto &chain = vertex.second[0], &blocks = vertex.second[1];  //要接收的链、要产生的块
            bool canDiffuse = canAccept(ans[v], chain) or not blocks.empty();  //节点v是否要向外广播主链
            if (canAccept(ans[v], chain))  //先接收其他节点的主链
                ans[v] = chain;
            for (int b : blocks)  //再产生块
                ans[v].push_back(b);
            if (canDiffuse)  //向外广播
                diffuse(v, curTime + t);
        }
    }
    actions.erase(actions.begin(), actions.upper_bound(b));  //删除b时刻及其以前的所有操作，避免重复处理
    cout << ans[a].size();
    for (int i : ans[a])
        cout << " " << i;
    cout << "\n";
}
int main() {
    ios::sync_with_stdio(false);
    cin >> n >> m;
    for (int i = 0; i < m; ++i) {
        int a, b;
        cin >> a >> b;
        graph[a].push_back(b);
        graph[b].push_back(a);
    }
    cin >> t >> k;
    for (int i = 0; i < k; ++i) {
        int a, b, c;
        cin >> a >> b;
        if (cin.get() == '\n' or cin.eof()) {
            query(a, b);
        } else {
            cin >> c;
            actions[b][a][1].push_back(c);
        }
    }
    return 0;
}


```
化学方程式
```language
#include <bits/stdc++.h>
using namespace std;
int n;
string formula;
unordered_map<string, int> ans;
//返回formula的[first,last]区间对应的数字,注意函数返回之后传递给first的实参将移动到第一个非数字字符的位置
int computeDigit(int& first, int last) {
    int i = 0;
    for (; first <= last and isdigit(formula[first]); ++first)
        i = i * 10 + formula[first] - '0';
    return i == 0 ? 1 : i;
}
void f(int first, int last, int e) {  //计算formula的[first,last]区间的原子及其对应系数，基本系数为e
    if (first == last or (last - first == 1 and islower(formula[last]))) {  //化学式是单个原子
        ans[formula.substr(first, last - first + 1)] += e;  //该原子个数递增e
        return;
    }
    e *= computeDigit(first, last);  //该化学式内所有原子基本系数要乘上该化学式起始系数
    for (int i = first, j = i + 1; i <= last; i = j, ++j) {  //遍历化学式
        if (isupper(formula[i])) {  //是原子
            if (j <= last and islower(formula[j]))
                ++j;
            int k = j;
            f(i, k - 1, e * computeDigit(j, last));  //递归处理
        } else if (formula[i] == '(') {  //遇到(
            for (int num = 1; num != 0; ++j) {  //找到对应的)位置存储在j中
                if (formula[j] == '(')
                    ++num;
                else if (formula[j] == ')')
                    --num;
            }
            int k = j;
            f(i + 1, k - 1, e * computeDigit(j, last));  //递归处理
        }
    }
}
void expression(int first, int last, int e) {  //按+分离出所有化学式
    for (int i = first, j = first; i <= last; i = j + 1) {
        j = formula.find('+', i);
        if (j == string::npos or j > last)
            j = last + 1;
        f(i, j - 1, e);
    }
}
int main() {
    cin >> n;
    while (n--) {
        cin >> formula;
        ans.clear();
        int k = formula.find('=');  //按=将方程式分割成两部分
        expression(0, k - 1, 1);
        expression(k + 1, formula.size() - 1, -1);
        //查找有没有原子对应个数不为0
        auto i = find_if(ans.begin(), ans.end(), [](const pair<string, int>& p) { return p.second != 0; });
        cout << ((i == ans.end()) ? "Y" : "N") << "\n";
    }
    return 0;
}
```
字符画
```language
#include <bits/stdc++.h>
using namespace std;
void output(string& s, array<int, 3> rgb = {0, 0, 0}) {  //输出
    for (char c : s)
        if (c == 'R' || c == 'G' || c == 'B') {  //是RGB数值
            string t = to_string(rgb[c == 'R' ? 0 : c == 'G' ? 1 : 2]);  //将数值转换成字符串
            for (char cc : t)  //遍历字符串
                printf("\\x%02X", cc);  //输出16进制数
        } else
            printf("\\x%02X", c);  //输出字符的16进制数
}
int main() {
    string back = "\x1b[48;2;R;G;Bm", reset = "\x1b[0m";  //背景色和重置默认值字符串
    int m, n, p, q;
    cin >> m >> n >> p >> q;
    vector<vector<array<int, 3>>> image(n);  //图像像素
    string rgb;
    for (int i = 0; i < n; ++i) {
        for (int j = 0; j < m; ++j) {
            cin >> rgb;
            if (rgb.size() == 2)  //只有2位字符
                rgb += string(5, rgb.back());  //字符串末尾添加5个末尾字符
            else if (rgb.size() == 4)  //只有4位字符
                rgb = "#" + string(2, rgb[1]) + string(2, rgb[2]) + string(2, rgb[3]);  //添加成为6位
            image[i].push_back({0, 0, 0});
            for (int t = 0; t < 3; ++t)  //计算RGB数值，将16进制数转换成10进制
                image[i].back()[t] = stoi(rgb.substr(2 * t + 1, 2), 0, 16);
        }
    }
    array<int, 3> last = {0, 0, 0}, start = {0, 0, 0};
    for (int i = 0; i < n / q; ++i) {  //遍历所有像素
        for (int j = 0; j < m / p; ++j) {
            array<int, 3> cur = {0, 0, 0};
            for (int r = 0; r < q; ++r) {  //计算块内RGB颜色分量之和
                for (int s = 0; s < p; ++s) {
                    for (int t = 0; t < 3; ++t)
                        cur[t] += image[i * q + r][j * p + s][t];
                }
            }
            for (int t = 0; t < 3; ++t)  //计算RGB颜色分量平均值
                cur[t] /= p * q;
            if (cur != last)  //和上一个块颜色分量不同
                if (cur == start)  //和默认颜色分量一致，输出重置转义序列
                    output(reset);
                else
                    output(back, cur);
            last = cur;  //更新上一个状态为当前状态
            printf("\\x%02X", ' ');  //每一个块后输出一个空格
        }
        if (last != start)  //每一行结束后恢复默认状态
            output(reset);
        last = start;  //每一行结束后更新上一个状态位默认状态
        printf("\\x%02X", '\n');  //每一行字符后输出一个换行
    }
    return 0;
}
```




