# Git教程
## 总结
git init
git add <file>  //可反复多次使用，添加多个文件。提交一次
git commit -m <message>

git status

git diff <file>

## 安装-配置Git
### 配置名字和Email地址
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"

## 创建版本库repository
* 创建空目录

  ```
  $ mkdir learngit
  $ cd learngit
  ```

* 初始化目录

  ```java
  $ git init  //把目录变成Git可以管理的仓库
  ```

  //out:Initialized empty Git repository in E:/WorkSpace/Study_node/Git/.git/
  **.git**文件为版本控制文件

  **note**:所有的版本控制系统，其实只能跟踪文本文件的改动，比如TXT文件，网页，所有的程序代码等等，Git也不例外。版本控制系统可以告诉你每次的改动，比如在第5行加了一个单词“Linux”，在第8行删了一个单词“Windows”。而图片、视频这些二进制文件，虽然也能由版本控制系统管理，但没法跟踪文件的变化，只能把二进制文件每次改动串起来，也就是只知道图片从100KB改成了120KB，但到底改了啥，版本控制系统不知道

* 将文件添加到repository

	```java
	$ git add 01Git.md
	$ git commit -m "wrote a 01Git.md file"	//-m 后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义的，这样你就能从历史记录里方便地找到改动记录
	```
	
	out:[master (root-commit) a38d374] wrote a 01Git.md file
	 1 file changed, 15 insertions(+)
	 create mode 100644 01Git.md

## Repository管理

### 版本回退

1. git status
2. git diff <file>

