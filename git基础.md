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

## 创建版本库

创建空目录，`pwd`命令用于显示当前目录:

<img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200918135435683.png" alt="image-20200918135435683" style="zoom:50%;" />

通过 `git init` 命令把这个目录变成Git可以管理的仓库：

![image-20200918141147373](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200918141147373.png)

如果你没有看到`.git`目录，那是因为这个目录默认是隐藏的，用`ls -ah`命令就可以看见，或在文件中查看隐藏项目。``![image-20200918141403980](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200918141403980.png)

<img src="C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200918140605236.png" alt="image-20200918140605236" style="zoom:80%;" />



## 本地推远程

- 命令把这个目录变成Git可以管理的仓库： `git init`  添加目录下所有：`git add . `  遇到警告(可不解决)，解决：`git config core.autocrlf true`  再次输入` git add . ` 则不跳警示

  ![1](C:\Users\dell\Desktop\github\截图\1.png)

- 查看仓库：`git status`

- 第一次：`git commit -m "first commit"`

- 查看仓库：`git status`   查看日志：`git log`   本地文件导入GitHub: 

  ```
  git remote add origin git@github.com:Ws1118/Novice.git  
  ```

   ![2](C:\Users\dell\Desktop\github\截图\2.png)

- 推送：`git push -u origin master`    本地文件导入GitHub: 

  ```
  git remote add origin git@github.com:Ws1118/quickstart.git
  ```

    

  ![3](C:\Users\dell\Desktop\github\截图\3.png)
- 若在 idea 中修改再次导入：`git commit -m "update index.jsp"`

## 远程推本地

- 远程在GitHub中修改完后
- 推送:  `git push -u origin master`
- 把远程修改的导入本地:  `git pull `

## git命令

工作区----`git add`----暂存区----`git commit`----本地库

[Git基本命令大全]https://shimo.im/docs/47kgJ29Op9iOGDqV/ 

`git init` 初始化git仓库,查看文件位置

`git add . `添加文件

`git commit -m"本次提交说明"`

`git status` 显示当前仓库最新状态

`git log` 查看日志

`git push -u origin master` 推送

`git pull` 把远程修改的导入本地

`git diff `查看指定文件具体修改哪些内容

`git show` 查看最后一个commit的修改

`git blame` 查看谁什么时间改了哪些文件

`git log` 显示从最近到最远的提交日志

`git reset` 跳转到某一版本

`git branch` 列出所有分支

`git checkout <branchName>` 切换分支

`git merge <branchName>` 合并分支

`git clone` 克隆远端仓库

```
git remote add origin git@github.com:Ws1118/Novice.git 
```

本地文件导入GitHub![Snipaste_2020-09-17_21-22-09](C:\Users\dell\Desktop\github\截图\Snipaste_2020-09-17_21-22-09.png)

## 如何将本地项目上传到GitHub

[如何将本地项目上传到GitHub]https://blog.csdn.net/u014135752/article/details/79951802

![image-20200918155030021](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200918155030021.png)

## 协作实践

- 本地操作
  - 创建文件夹：`learn_git`  进入，打开Git Bash Here  创建文件夹：`command-pratice` 进入 ` command-pratice `  创建一些文件，`target`中创建文件` system.dll`![image-20200918220207139](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200918220207139.png)
  - 查看仓库：`git status` 添加 提交：`git add .  ` 加备注：`git commit -m "init" ` 
  - 查看仓库：`git status`  状态为  clean  可进行下一步操作（本地操作完成）

![image-20200918221341805](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200918221341805.png)

- 远程操作
  - 远程创建 添加远程仓库并提交、推送![image-20200918223301330](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200918223301330.png)
  - 远程刷新

- 添加项目协作者

  - 进入远程需要协作的仓库，`Setting`  `Manage access`   `Invite a collaborator`邀请协作者

    ![image-20200918224123695](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200918224123695.png)

- 协作者克隆项目并编辑提交推送

  - HTTPS 模式需要输入密码  所以一般使用SSH模式 复制![image-20200918230023000](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200918230023000.png)

  - 在文件需创建位置 打开Git Bash Here  克隆`get clone 上面复制内容`   即可看见克隆文件

    ![image-20200918230532547](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200918230532547.png)

  - 打开克隆文件，加入文件。在克隆文件中，打开Git Bash Here  添加文件，查看仓库，添加说明![image-20200918231701559](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200918231701559.png)
  - 查看仓库状态  clean 进行下一步![image-20200918231853097](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200918231853097.png)
  - 推送（版本问题会报错）![image-20200918232203545](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200918232203545.png)
  - -- 插入 --   位置输入 i   再按 esc 键,输入  :wq![image-20200918232448519](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200918232448519.png)
  - 继续推送 `git push origin master` 推送成功，刷新GitHub

- 多人编辑一行数据
  
- 将克隆文件编辑结束后， 提交：`git add .  `   加备注：`git commit -m "init"  ` 推送 `git push origin master`（版本问题会报错）把远程修改的导入本地：`git pull`  再次推送： `git push origin master`，报错 打开修改文件，手动删除乱码。提交：`git add .  `   加备注：`git commit -m "init"  `查看仓库状态：`git status `   为 clean  推送 `git push origin master`  推送成功，刷新GitHub
  
- 多分支协作流程

  - 在本地创建新的分支

    - 查看当前分支：`git branch`提交：`git add .  `   加备注：`git commit -m "init"  `创建分支 `dev`：`git branch dev`  查看当前分支：`git branch`  进入`dev` 分支：`git checkout dev`  创建`soft`文件夹：![image-20200919142944119](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200919142944119.png)

      提交：`git add .  `   加备注：`git commit -m "init"  `  查看仓库状态：`git status `    推送：`git push --set-upstream origin dev`    远程刷新。

- 协作者在DEV分支开发
  
- 推送：`git pull`  查看分支： `git branch`  创建分支：`git checkout dev`  查看分支：`git branch` 提交：`git add .  `   加备注：`git commit -m "init"  `   推送：`git push origin dev`  推送： `git pull`![image-20200919170549049](C:\Users\dell\AppData\Roaming\Typora\typora-user-images\image-20200919170549049.png)
  
- 分支的合并
  
- （dev分支合并到master分支）`git checkout master`  `git merge dev`  `git add .` `git commit -m "  "`  `git pull`  `git status`  `git push`  远程刷新。
  
- 本地和远程分支的删除
  - 删除本地:`git branch -d dev`  查看：`git branch`
  - 删除远程：:`git branch -r -d dev` `git push origin :dev`![Snipaste_2020-09-19_17-24-08](C:\Users\dell\Desktop\Snipaste_2020-09-19_17-24-08.png)