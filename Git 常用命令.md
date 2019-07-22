# Git常用命令

## 配置用户信息

- 配置用户名

  `git config --global user.name "liulidong"`

- 配置邮箱

  `git config --global user.email "lidong.liu@hand-china.com"`

- 查看所有配置

  `git config list`

## 创建版本库

- 初始化一个Git仓库

  `git init`

- 添加文件到Git仓库

  `git add <file>` 

  `git add .`

- 将文件提交到仓库

  `git commit -m "<message>"`

## 版本管理

- 在版本的历史之间穿梭，HEAD指向的就是当前版本

  `git reset --hard commit_id `

- 查看提交历史

  `git log`

- 查看命令历史

  `git reflog`

- 查看Git状态

  `git status`

- 撤销修改

  1. 修改还未`add`到暂存区，执行`git checkout -- <filename>`撤销修改

  2. 修改已经`add`到暂存区，又作了修改，此时之下`git checkout -- <filename>`会回到上一次添加到暂存区的状态

  3. 修改已经add到暂存区，又作了修改，但是想丢弃修改，则执行

     `git reset HEAD <filename>`

- 在Git仓库里面删除一个文件

  `git rm <filename>`

## 远程仓库

- 关联一个远程仓库

  `git remote add origin git@server-name:path/repo-name.git `

- 关联后，使用`git push -u origin master` 第一次推送master分支的所有内容，`-u`设置默认远程仓库，之后推送就可以使用`git push origin master`

- 克隆一个仓库

  `git clone`

- Git支持多种协议，包括`https`，但通过`ssh`支持的远程`git`协议速度最快

## 分支管理

- 创建分支

  `git branch develop`

- 切换分支

  `git checkout develop`

- 创建develop分支同时切换到develop分支

  `git checkout -b develop`

- 查看当前分支

  `git bracnch`

- 合并develop分支到当前分支上

  `git merge develop`

- 删除分支

  `git branch -d develop`

- 查看分支合并图

  `git log --graph`

- 储藏当前工作现场

  `git stash`

- 查看存储的工作现场

  `git stash list`

- 恢复工作现场

  `git stash apply`

- 删除stash内容

  `git stash drop`

- 恢复工作现场的同时把stash的内容删了

  `git stash pop`

- 可以多次stash，恢复的时候可以先用`git stash list`查看，然后恢复指定的stash

  `git stash apply stash@{0}`

- 丢弃一个没有被合并过的分支

  `git branch -D <name>`

- 推送本地分支的修改

  `git push origin <branch-name>`

- 如果推送失败，则因为远程分支比本地的库更新，需要先`git pull`到本地试图合并

- 如果合并有冲突，则解决冲突，并在本地提交，再次推送

- 如果`git pull`提示`no tracing information`，则说明本地分支和远程分支的链接关系没有创建,用命令`git branch --set-upstream-to <branch-name> origin/<branch-name>`

- 查看远程库信息

  `git remote -v`

- `git rebase`操作可以把本地未push的分叉提交历史整理成直线

## 标签管理

- `git tag <tagname>`新建一个标签，默认为`HEAD`，也可以指定一个`commit_id`
- `git tag -a <tagname> -m "<taginfo>"`可以指定标签信息
- `git tag`查看所有标签
- `git push origin <tagname>`可以推送一个本地标签
- `git push origin --tags`可以推动全部未推送过的本地标签
- `git tag -d <tagname>`可以删除一个本地标签
- `git push orign :refs/tags/<tagname>`可以删除一个远程标签



