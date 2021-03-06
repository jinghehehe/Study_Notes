**远程服务器运行神器tmux技巧总结**
**********************************************
- 在服务器运行代码时，通常需要在运行的同时进行其他操作，网上通常的做法是将程序挂在后台，如采用nohup command &的方式，使其
  退出账户时依然继续运行，但前提是exit正常退出才可以，异常退出依然不能保证继续运行。本文将针对tmux这种可以不间断后台运行程
  序方式进行操作说明及常用指令的介绍。

- Tmux 是一个终端复用器（terminal multiplexer），非常有用，属于常用的开发工具。类似的终端复用器还有 GNU Screen。Tmux 与
  它功能相似，但是更易用，也更强大。
- 常用的窗口终端运行，都是一次会话，窗口与会话中的进程是连在一起的，打开窗口，会话开始，关闭窗口，会话结束。Tmux 就是会话与
  窗口的"解绑"工具，将它们彻底分离。


- 其主要功能有以下4点：
	1. 它允许在单个窗口中，同时访问多个会话。这对于同时运行多个命令行程序很有用。
	2. 它可以让新窗口"接入"已经存在的会话。
	3. 它允许每个会话有多个连接窗口，因此可以多人实时共享会话。
	4. 它还支持窗口任意的垂直和水平拆分。

- 基本用法：
	- 安装：
	```language
	# Ubuntu 或 Debian
	$ sudo apt-get install tmux

	# CentOS 或 Fedora
	$ sudo yum install tmux

	# Mac
	$ brew install tmux
	```
	
	- 启动与退出：
	安装完成后，键入tmux命令，就进入了 Tmux 窗口。按下Ctrl+d或者显式输入exit命令，就可以退出 Tmux 窗口
	```language
	$ tmux
	$ exit
	```

- 会话管理：
	这里主要列举几个常用指令，具体指令会在后文链接补充。
	- 新建会话：
	第一个启动的 Tmux 窗口，编号是0，第二个窗口的编号是1，更好的方法是为会话起名。
	```language
	$ tmux new -s <session-name>
	```
	- 分离会话：
	在 Tmux 窗口中，按下Ctrl+b d或者输入tmux detach命令，就会将当前会话与窗口分离。命令执行后，就会退出当前
 	Tmux 窗口，但是会话和里面的进程仍然在后台运行。
	```language
	$ tmux detach
	```
	tmux ls命令可以查看当前所有的 Tmux 会话。
	```language
	$ tmux ls
	```	
	- 接入会话：
	tmux attach命令用于重新接入某个已存在的会话
	```language
	# 使用会话名称
	$ tmux attach -t <session-name>
	```	
	- 杀死会话：
	tmux kill-session命令用于杀死某个会话
	```language
	# 使用会话名称
	$ tmux kill-session -t <session-name>
	```	
	- 切换会话：
	tmux switch命令用于切换会话
	```language
	# 使用会话名称
	$ tmux switch -t <session-name>
	```

- 最简操作流程：
	1. 新建会话tmux new -s my_session
	2. 在 Tmux 窗口运行所需的程序
	3. 按下快捷键Ctrl+b d将会话分离或tmux detach
	4. 下次使用时，重新连接到会话tmux attach -t my_session。


- 参考文献
	[tmux详细操作说明](http://www.ruanyifeng.com/blog/2019/10/tmux.html)
	[linux后台运行&和nohup操作说明](https://blog.csdn.net/liuyanfeier/article/details/62422742)





	


	


