# Linux指令知识点总结
***
## 本文用于记录下Linux系统下需要用到的部分指令。（不定时补充更新）

### shell脚本执行命令
- 脚本使用/bin/bash来解释执行
```language
#！/bin/bash 
```

### shell脚本执行方式
- 利用./来执行
```language
./script.sh  
```
- 利用bash(sh)来执行脚本
```language
sh script.sh 或 bash script.sh 
```
- 利用source或. 来执行
```language
source script.sh 
. script.sh 
```
- 上面第三种方式不启用新的shell，在当前shell中执行，设定的局部变量在执行完命令后仍然有效。bash 或 sh 或 shell script 执行时，另起一个子shell，其继承父shell的环境变量，其子shelll的变量执行完后不影响父shell。


### shell脚本中的 exec 命令
- exec 是 bash 的内置命令，shell 的内件命令exec执行命令时，不启用新的shell进程。
- exec是用被执行的命令行替换掉当前的shell进程，且exec命令后的其他命令将不再执行。例如在当前shell中执行 exec ls  表示执行ls这条命令来替换当前的shell ，即为执行完后会退出当前shell。为了避免这个结果的影响，一般将exec命令放到一个shell脚本中，用主脚本调用这个脚本，调用处可以用bash  xx.sh(xx.sh为存放exec命令的脚本)，这样会为xx.sh建立一个子shell去执行，当执行exec后该子脚本进程就被替换成相应的exec的命令。其中有一个例外：当exec命令对文件描述符操作的时候，就不会替换shell，而是操作完成后还会继续执行后面的命令！

参考链接：[exec](https://www.jianshu.com/p/ca012415cd5f)
- exec与system的区别
1. exec是直接用新的进程去代替原来的程序运行，运行完毕之后不回到原先的程序中去。
2. system是调用shell执行你的命令，system=fork+exec+waitpid,执行完毕之后，回到原先的程序中去。继续执行下面的部分。
3. system 是在单独的进程中执行命令，完了还会回到你的程序中。而exec函数是直接在你的进程中执行新的程序，新的程序会把你的程序覆盖，除非调用出错，否则你再也回不到exec后面的代码，就是说你的程序就变成了exec调用的那个程序了。


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
其他 3-9 都是空白描述符。默认情况下，command > file 将 stdout 重定向到 file，command < file 将stdin 重定向到 file。

- 如果希望执行某个命令，但又不希望在屏幕上显示输出结果，那么可以将输出重定向到 /dev/null：
```language
$ command > /dev/null
```
/dev/null 是一个特殊的文件，写入到它的内容都会被丢弃；如果尝试从该文件读取内容，那么什么也读不到。但是 /dev/null 文件非常有用，将命令的输出重定向到它，会起到"禁止输出"的效果。如果希望屏蔽 stdout 和 stderr，可以这样写：
```language
$ command > /dev/null 2>&1
```


