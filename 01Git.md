# Git教程
## 总结
学习网址：https://www.liaoxuefeng.com/wiki/896043488029600
```

$ git init
$ git add <file>  //可反复多次使用，添加多个文件。提交一次
$ git commit -m <message>
$ git status
$ git diff <file>
    
    
$ git checkout -b dev	//创建并切换分支
git switch -c dev		//创建并切换分支
/*
等同于
$ git branch dev		//创建dev分支
$ git checkout dev		//切换到dev分支
$ git switch dev		//切换到dev分支,建议使用这个	
*/
    
$ git branch			//查看分支
$ git merge dev			//合并：命令用于合并指定分支到当前分支。合并后，再查看readme.txt的内容，就可以看到，和dev分支的最新提交是完全一样的。
$ git branch -d dev		//合并后删除分支
    
# git branch dev
# git switch dev
# git stash		//保存当前工作现场
# git stash list 
# git stash apply //恢复现场
# git stash apply stash@{0}//恢复指定现场
# git stash pop   //删除stash并恢复现场
# git cherry-pack 4c805e2	// 复制一个特定的提交到当前分支
远程协助
$ git remote
$ git remote -v
$ git push origin main
$ git push origin dev
$ git clone git@github.com:michaelliao/learngit.git
$ git checkout -b dev origin/dev	//创建远程origin的dev分支到本地
```





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

3. git log 

   1. 查看提交到Git仓库的版本数量

   2. git log --pretty=oneline

      **[out]**:27ef872791a51baa20b335e820f44b0dbbae872b (HEAD -> master, origin/master, origin/HEAD) my first commit
      		1c3885b280e1f0345a1b455488a77479b3784d3b Initial commit

4. git reset --hard HEAD^

   1. 退回上一个版本

5. git rest --hard 27ef872791

   1. 退回指定版本

6. git reflog

   1. 查看命令历史

## 分支管理

### 创建、切换、查看、合并

```
$ git checkout -b dev	//创建并切换分支
/*
等同于
$ git branch dev		//创建dev分支
$ git checkout dev		//切换到dev分支
$ git switch dev		//切换到dev分支	
*/
$ git branch			//查看分支
$ git merge dev			//合并：命令用于合并指定分支到当前分支。合并后，再查看readme.txt的内容，就可以看到，和dev分支的最新提交是完全一样的。
$ git branch -d dev		//合并后删除分支

$ git branch fdy
$ git switch fdy
$ git add .
$ git commit -m "commit fdy of branch"
$ git switch main
$ git log --graph	//查看分支合并图
/*
git 用<<<<<,=======,>>>>>>标出不同分支内容，手动修改后可再次提交解决冲突
当git
*/
```

### 解决分支冲突

```java
$ git branch fdy
$ git switch fdy
$ git add .
$ git commit -m "commit fdy of branch"
$ git switch main
$ git log --graph	//查看分支合并图
/*
git 用<<<<<,=======,>>>>>>标出不同分支内容，手动修改后可再次提交解决冲突
当git
*/
```

### Bug分支

保持当前分支上下文，创建bug分支修复main分支的bug

```java
# git branch dev
# git switch dev
# git stash		//保存当前工作现场
# git stash list 
# git stash apply //恢复现场
# git stash apply stash@{0}//恢复指定现场
# git stash pop   //删除stash并恢复现场
# git cherry-pack 4c805e2	// 复制一个特定的提交到当前分支

/*
修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；
当手头工作没有完成时，先把工作现场git stash一下，然后去修复bug，修复后，再git stash pop，回到工作现场；
在master分支上修复的bug，想要合并到当前dev分支，可以用git cherry-pick <commit>命令，把bug提交的修改“复制”到当前分支，避免重复劳动。
*/
```

### 多人协作

```
$ git remote
$ git remote -v
$ git push origin main
$ git push origin dev
$ git clone git@github.com:michaelliao/learngit.git
$ git checkout -b dev origin/dev	//创建远程origin的dev分支到本地
```

**多人协作工作模式**

1. 首先，可以试图用`git push origin <branch-name>`推送自己的修改；
2. 如果推送失败，则因为远程分支比你的本地更新，需要先用`git pull`试图合并；
3. 如果合并有冲突，则解决冲突，并在本地提交；
4. 没有冲突或者解决掉冲突后，再用`git push origin <branch-name>`推送就能成功！

如果`git pull`提示`no tracking information`，则说明本地分支和远程分支的链接关系没有创建，用命令`git branch --set-upstream-to <branch-name> origin/<branch-name>`。



**小结**

- 查看远程库信息，使用`git remote -v`；
- 本地新建的分支如果不推送到远程，对其他人就是不可见的；
- 从本地推送分支，使用`git push origin branch-name`，如果推送失败，先用`git pull`抓取远程的新提交；
- 在本地创建和远程分支对应的分支，使用`git checkout -b branch-name origin/branch-name`，本地和远程分支的名称最好一致；
- 建立本地分支和远程分支的关联，使用`git branch --set-upstream branch-name origin/branch-name`；
- 从远程抓取分支，使用`git pull`，如果有冲突，要先处理冲突。
