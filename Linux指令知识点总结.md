# Linux指令知识点总结
***
## 本文用于记录下Linux系统下需要用到的部分指令。（不定时补充更新）

### shell脚本中的 exec 命令
- exec 是 bash 的内置命令，shell 的内件命令exec执行命令时，不启用新的shell进程。



### Shell 输入/输出重定向
输出重定向是大于号(>)，输入重定向是小于号(<)。
|命令|说明|
|-|-|
|command > file	| 将输出重定向到 file。|
|command < file	|将输入重定向到 file。|
|command >> file |将输出以追加的方式重定向到 file。|
|n > file	|将文件描述符为 n 的文件重定向到 file。|
|n >> file	|将文件描述符为 n 的文件以追加的方式重定向到 file。|
|n >& m	|将输出文件 m 和 n 合并。|
|n <& m	|将输入文件 m 和 n 合并。|
|<< tag	|将开始标记 tag 和结束标记 tag 之间的内容作为输入。|
