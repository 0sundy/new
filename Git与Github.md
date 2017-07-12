# Git与Github

## 1 Git

### 1.1 安装Git

Windows下安装msysGit，选择Use Git Bash only，Checkout Windows-style, commit Unix-style line endings

### 1.2 设置姓名和邮箱

配置方法：git config --global<配置名称><配置的值>

````
git config --global user.name "Ahora Wang"
git config --global user.email "lzyz09193@163.com"
````

### 1.3 让命令输出有更高的可读性

````
git config --global color.ui auto
````

### 1.4 连接到Github

1. 创建Github账户；
2. 设置头像；
3. 设置SSH KEY；

	````
	ssh-keygen -t rsa -C "your_email@example.com"
	````
	按回车，输入密码，再次输入密码
	
	生成：
	
	- id_rsa 是私有密钥
	- id_rsa.pub是公开密钥

4. 在Github上添加公开密钥；
5. 添加成功后，会接到一封邮件；
6. 用私人密钥和Github通信

	````
	ssh -T git@github.com
	````
	
	显示如下结果为成功
	
	>Hi xxx! You've successfully authenticated, but GitHub dose not provide shell access.

### 1.5 clone已有仓库

````
git clone xxxx
````

编写代码后

````
git status
git add xxxx
git commit -m "xxxx"
git log
````

推送到github

````
git push
````

**git pull命令执行两个操作: 它从远程分支(remote branch)抓取修改git fetch的内容，然后把它合并git merge进当前的分支。**

### 1.6 Git基本操作

初始化仓库
````
git init
````

仓库状态

````
git status
````

向暂存区添加文件

````
git add
````

将暂存区中的函数保存到仓库的历史记录

````
git commit -m "提交信息"
````

若不加 -m，则在打开的编辑器中

- 第一行：用一行文字简述更改内容
- 第二行：空行
- 第三行：记述更改原因和详细内容

#### 查看提交日志

````
git log
````

**git log查看远程分支做的所有修改**

只显示提交信息第一行

````
git log --pretty=short
````

只显示指定目录、文件的日志

````
git log README.md
````

显示文件的改动

````
git log -p
````

#### 查看更改前后差别

查看工作树和暂存区的差别

````
git diff
````

查看工作树和最新提交的差别

````
git diff HEAD
````

git commit之前先执行git diff HEAD命令，查看本次提交与上次提交的差别。HEAD是指向最新一次提交的指针。

### 1.7 分支操作

显示分支一览表

````
git barnch
````

创建切换分支

````
git checkout -b feature-A
````

等价于
````
git branch feature-A
git checkout feature-A
````

切换分支

````
git checkout master
git checkout -
````

- 特性分支：用于实现某个特定功能的开发。
- 稳定分支：用于提供稳定版本。

合并分支

````
git merge --no-ff feature-A
````

以图表形式查看分支

````
git log --graph
````

回溯历史版本
````
git reset --hard 哈希值
````

合并时可能出现冲突，解决冲突，执行git add与git commit。

### 1.8 推送至远程仓库

添加远程仓库

````
git remote add origin xxxx.git
````

#### 推送至远程仓库

推送至master分支

````
git push -u origin master
````

推送至master以外分支

````
git checkout -b feature-D
````

#### 从远程仓库获取

````
git clone xxxx
````

获取远程的feature-D分支

````
git checkout -b feature-D origin/feature-D
````

向本地的feature-D分支提交更改

推送feature-D分支

````
git push
````

#### 从远成仓库获取最新状态

````
git pull
````
