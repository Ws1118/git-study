# git基础

## 	git`安装`

下载地址：[https://git-scm.com/downloads](https://git-scm.com/downloads)

环境变量C:\Program Files\Git\cmd

启动命令行，输入：git --version：

<img src="C:\Users\dell\Desktop\Snipaste_2020-09-17_15-50-10.png" style="zoom:67%;" />

桌面右击打开Git Bash Here：

<img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200917155545715.png" alt="image-20200917155545715" style="zoom: 67%;" />

## git`基础命令学习`

新建文件夹learn_git，右击打开Git BAsh

<img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200917162126591.png" alt="image-20200917162126591" style="zoom: 33%;" />

输入git init，看到隐形文件夹.git

<img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200917162335279.png" alt="image-20200917162335279" style="zoom: 50%;" />

若没有.git

<img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200917162702186.png" alt="image-20200917162702186" style="zoom:50%;" />

建文档：

![image-20200917162849280](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200917162849280.png)

文件入仓库的暂存区：

<img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200917163112322.png" alt="image-20200917163112322" style="zoom:50%;" />

# 创建版本库

创建空目录，`pwd`命令用于显示当前目录:

<img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200918135435683.png" alt="image-20200918135435683" style="zoom:50%;" />

通过 `git init` 命令把这个目录变成Git可以管理的仓库：

![image-20200918141147373](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200918141147373.png)

如果你没有看到`.git`目录，那是因为这个目录默认是隐藏的，用`ls -ah`命令就可以看见，或在文件中查看隐藏项目。``![image-20200918141403980](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200918141403980.png)

<img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200918140605236.png" alt="image-20200918140605236" style="zoom:80%;" />



``