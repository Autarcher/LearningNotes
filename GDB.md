# 命令

`r`(run): 运行当前文件

`n`(next):进入下一步（不进入调用函数）

`s`(step):进入下一步且进入调用函数

`finish`:跳出当前执行的函数

# GDB小技巧 

1. shell脚本：

里面在开始写一个shell可以执行linux的命令如ls，cat等

eg：

![image-20240711094902513](C:\Users\廖一奥\AppData\Roaming\Typora\typora-user-images\image-20240711094902513.png)

2. 日志功能：

set logging on  [log_name]

如果不设置log_name则自动创建一个gdb.txt文件把所有调试信息保存进去

3. watchpoint:

观察变量值的改变

# 如何调试挂掉的进程和一个正在运行的程序

## 调试一个core文件（挂掉的文件）

电脑是多人共享的所以有限制

`ulimit -a` 查看所有用户的shell的限制（可能有core限制）

![image-20240711181716198](C:\Users\廖一奥\AppData\Roaming\Typora\typora-user-images\image-20240711181716198.png)

记得打开当前文件的读写权限  `chmod u+x`

调试方法：

`gdb [file_name] [core_name]`

eg:![image-20240711181606011](C:\Users\廖一奥\AppData\Roaming\Typora\typora-user-images\image-20240711181606011.png)

不懂的命令先用`man`指令查。

## 调试一个正在运行的进程

`./test & `表示在后台运行test文件

会显示他的进程号

eg:![image-20240711183202237](C:\Users\廖一奥\AppData\Roaming\Typora\typora-user-images\image-20240711183202237.png)

也可以用 `pd -ef | grep test` 参看test开头的所有文件的服务情况。

![image-20240711183257371](C:\Users\廖一奥\AppData\Roaming\Typora\typora-user-images\image-20240711183257371.png)