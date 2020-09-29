# DFS与BFS比较知识点汇总
***
dfs比bfs在使用情况下更常见，空间复杂度更低。
dfs通常用于递归，其等价方式迭代通常采用stack实现。
但bfs有两种适用场景：层序遍历和最短路径。Dijkstra 算法解决的是带权最短路径问题，而我们这里关注的是无权最短路径问题。也可以看成每条边的权重都是 1。这样的最短路径问题，用 BFS 求解就行了。


https://mp.weixin.qq.com/s?__biz=MzA5ODk3ODA4OQ==&mid=2648167208&idx=1&sn=d8118c7c0e0f57ea2bdd8aa4d6ac7ab7&chksm=88aa236ebfddaa78a6183cf6dcf88f82c5ff5efb7f5c55d6844d9104b307862869eb9032bd1f&token=1064083695&lang=zh_CN#rd

https://leetcode-cn.com/problems/binary-tree-level-order-traversal/solution/bfs-de-shi-yong-chang-jing-zong-jie-ceng-xu-bian-l/

https://mp.weixin.qq.com/s/c_zCrGHIVlBjUH_hJtghCg