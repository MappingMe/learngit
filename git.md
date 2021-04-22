# git

## git概述

- git功能：帮助管理修改先后文件，可以多人修改

- 集中式和分布式版本控制：
  - 集中式是只有一个中心服务器，所有人上传下载版本从SVN服务器。
  - 分布式没用中心服务器，每一个人的电脑都有一个服务器，为了方便可以定一个服务器为中心服务器
  
  ## git概念
  
- 工作区Working Directory：即是.git所在的那个目录，可以增加修改文件

- 版本库Repository：.git即是一个版本库，里面有一个暂存区

- 暂存区Index：当使用add标记文件时，其实就是提供到暂存区里面

- 当前分支Master：Git自动为我们创建了唯一一个`master`分支，commit就是往分支上提交更改。

## git语法

```java
$git init  //创建仓库
$git add '文件名' //把目录下文件提交到仓库
$git commit -m '描述' //把暂存区所有修改提交到仓库
$git status //获得仓库内文件的状态，不可查看修改内容
    	Changes not staged for commit:
		//说明该文件夹的修改未被提交
		Changes to be committed:
		//说明被add标记了，还没committed
		nothing to commit, working tree clean
		//说明没有被修改的文件未提交
$git diff '文件名'//获得该文件修改的内容
$git log  --pretty=oneline //获取仓库文件被修改的日志，获得版本号，加上参数可以简略点
$git reset --hard 版本号//回到指定的版本，回到旧版本后可打入新版本号回到新版本
$git reflog  //查看命令历史，以便确定要回到未来的哪个版本。
$git checkout -- file//这个文件回到最近一次git commit或git add时的状态,若没add则返回版本库状态
$git reset HEAD <file>//把add到暂存区的文件撤销暂存，此时文件恢复再add之前的状态
$git rm test.txt //把rm修改存放到暂存区
$git config --global color.ui true //让git适当显示不同颜色区分
$git config --global alias.st status //把st设计为status的别名
```

## 远程仓库

语法：

```java
$git remote add origin git@github.com:MapperMe/learngit.git //连接远程仓库
$git push -u origin master //把本地版本库上传到远程仓库，第一次推送所有内容
//使用命令git push origin master推送最新修改
$git remote -v //查看远程库信息
$git remote rm origin //根据名字删除
问题展示：error: failed to push some refs to 'gitee.com:zkpthink/git-test.git'
$git pull --rebase origin master//再推送
$git clone git@github.com:michaelliao/gitskills.git
```

## 分支管理

- 概念：创建一个分支，则存在分支和master分支两个分支，分支上提交修改，不影响master分支。

  ```java
  $git checkout -b dev //创建并切换到一个分支
  $git switch -c dev //创建并切换到一个分支
  $git branch //查看所有分支
  $git checkout master//切换分支
  $git switch master//切换分支
  $git branch  -d dev//删除分支
  $git merge dev //合并分支到master
  ```

- 分支冲突：
  - 当master和分支在同一个修改上存在矛盾的时候，使用merge合并会产生冲突。
  - git log --graph --pretty=oneline --abbrev-commit：可以通过日志查看合并情况。

- 分支合并模式：
  - 普通合并下，合并时将master指针指向dev指针指向的内容而已。
  - git merge --no-ff -m "描述"，合并时创建了一个新的空间并把指针指向这个空间。

- 环境暂时保存和恢复：

  ```java
  $git stash //把当前所做修改存储起来
  $git stash list //查看所有存储起来的修改
  $git stash apply //恢复修改但不删除备份
  $git stash drop//删除修改备份
  $git stash  pop//恢复最顶端修改并且删除此备份
  $cherry-pick //把某个提交修改复制到特定分支
  $git branch -D <name> //删除一个还未合并过的分支
  ```
  
  ## 多人协作
```
1. git checkout -b dev origin/dev  创建分支到本地
2. 首先，可以试图用`git push origin <branch-name>`推送自己的修改；
3. 如果推送失败，则因为远程分支比你的本地更新，需要先用`git pull`试图合并；
4. 如果合并有冲突，则解决冲突，并在本地提交；
5. 没有冲突或者解决掉冲突后，再用`git push origin <branch-name>`推送就能成功！

如果`git pull`提示`no tracking information`，则说明本地分支和远程分支的链接关系没有创建，用命令`git branch --set-upstream-to <branch-name> origin/<branch-name>`。

6.Rebase:通过把push的修改记录放在本地修改之前，使得提交记录git log --graph --pretty=oneline --abbrev-commit变成一条清晰的直线。

```
## 标签管理

标签含义：不可移动的、与commit指针绑定在一起的、名字可具意义的标签

创建标签：

```java
$ git tag v1.0 //切换到需要打标签的分支上
$ git tag //查看所有标签
$ git tag v0.9 f52c633 //通过git log获取过去commitID，可为过去的版本打上标签
$ git show <tagname> //获取tag的详细信息
$ git tag -a v0.1 -m "version 0.1 released" 1094adb //创建带有说明的标签
$ git push origin [tagname]//把本地指定标签上传到远程仓库
$ git push origin --tags//上传所有标签
$ git tag -d v0.1 //删除指定标签
//删除已经上传到远程的标签：
$ git tag -d v0.1 //先删除本地标签
$ git push origin :refs/tags/v0.9 //通过push删除远程标签
```


