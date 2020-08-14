# Linux指令知识点总结
***
## 本文用于记录下Linux系统下需要用到的部分指令。（不定时补充更新）

### shell脚本中的 exec 命令
- exec 是 bash 的内置命令，shell 的内件命令exec执行命令时，不启用新的shell进程。



### Shell 输入/输出重定向
- 输出重定向是大于号(>)，输入重定向是小于号(<)。默认键盘获取输入，屏幕输出。
- 如果不希望文件内容被覆盖，可以使用 >> 追加到文件末尾
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

#### 重定向深入讲解
一般情况下，每个 Unix/Linux 命令运行时都会打开三个文件：
- 标准输入文件(stdin)：stdin的文件描述符为0，Unix程序默认从stdin读取数据。
- 标准输出文件(stdout)：stdout 的文件描述符为1，Unix程序默认向stdout输出数据。
- 标准错误文件(stderr)：stderr的文件描述符为2，Unix程序会向stderr流中写入错误信息。
默认情况下，command > file 将 stdout 重定向到 file，command < file 将stdin 重定向到 file。
