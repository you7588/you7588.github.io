---
title: Git-Recipes
date: 2017-09-06 09:44:41
tags: [git, 常用, cheat sheet]## 配置
---

## 配置
>  三种方式

**系统（System）配置：**

```
$ git config --system --list                                 # 列出系统配置
```

文件路径：`/etc/gitconfig`（系统中对所有用户都普遍适用的配置）

**全局（Global）配置：**

```
$ git config --global user.name xxx                           # 设置用户名
$ git config --global user.email xxx@xxx.com                  # 设置用户邮箱
$ git config --global --list                                  # 列出全局配置
```

文件路径：`~/.gitconfig`（用户目录下的配置文件只适用于该用户）

**项目（Repository）配置：**

```
$ git config user.name "xxx"                                  # 设置用户名
$ git config user.email xxxx@xxx.com                          # 设置用户邮箱
$ git config --local --list                                   # 列出项目配置
```

文件路径：`<工作目录>/.git/config`（这里的配置仅仅针对当前项目有效）

**列出已有的配置：**

```
$ git config --list
```
<!--more-->

------


## 创建

 **复制一个已创建的远程仓库:**

```
# 通过 SSH
$ git clone ssh://user@domain.com/repo.git
$ git clone user@domain.com:repo.git                # Git会默认使用SSH及用当前登录的用户名连接服务器。

# 通过 HTTP
$ git clone http://domain.com/user/repo.git
```

文件路径：`当前目录/repo/.git`

 **在工作目录中初始化（创建）新的本地仓库:**

```
$ git init                                            # 创建文件夹，确保在工作目录里输入
```

文件路径：`当前目录/.git`

------

## 本地修改

 **检查当前文件状态**

```
$ git status                                          # 要确定哪些文件当前处于什么状态
```

**查看具体修改了什么地方**

```bash
# 查看未暂存的更新（git add之前输入）
$ git diff                                            # q 退出                      
# 查看已暂存的更新（git add之后输入）                                
$ git diff --staged    
# 查看预览差异，在合并改动之前
$ git diff <source_branch> <target_branch>              
```

**跟踪新文件**

```
$ git add xxx                      # 可以指明要跟踪的文件或目录（该目录下的所有文件）
$ git add .                        # 把所有新档案和改过的档案加进追踪修订，但“保留”删掉的档案。
$ git add -A                       # 全部加进追踪修订，包括删掉的档案。
$ git add -p xxx                   #### 把对某个文件的修改添加到下次提交中  
```

>  `git add` 是个多功能命令，根据目标文件的状态不同，此命令的效果也不同：
>  1)可以用它开始跟踪新文件(未曾跟踪过的文件标记为需要跟踪)
>  2)把已跟踪的文件放到暂存区,即把目标文件快照放入暂存区域(add file into staged area)
>  3)用于合并时把有冲突的文件标记为已解决状态等

**提交更新**

```
$ git commit -m 'xxx'                      # 附加消息提交
```

**跟踪+提交更新**

```
$ git commit -a -m 'xxx'                   # 直接跳过使用暂存区域
```

**修改最后一次提交**

```
$ git commit --amend                      ####  请勿修改已发布的提交记录!
```

**移除文件**

从暂存区域移除：
```
$ rm grit.gemspec                         #### 只是简单地从工作目录中手工删除文件（变为未暂存）
$ git rm <file>                           #### 记录此次移除文件的操作
```

若删除之前修改过并且已经放到暂存区域：
```
$ git rm  -f                              #### 强制删除（防误删除文件后丢失修改的内容）
```

```
rm -rf .git                               #### cd到需要删除git的目录，并运行命令
```

把文件从暂存区域移除，但仍然希望保留在当前工作目录中：
```
$ git rm --cached xxx        # 列出文件或者目录的名字
$ git rm log/\*.log          # glob 模式，此命令删除所有log/目录下扩展名为 .log 的文件
# 注意到星号 `*` 之前的反斜杠 `\`，因为 Git 有它自己的文件模式扩展匹配方式，所以我们不用 shell 来帮忙展开（译注：实际上不加反斜杠也可以运行，只不过按照 shell 扩展的话，仅仅删除指定目录下的文件而不会递归匹配。上面的例子本来就指定了目录，所以效果等同，但下面的例子就会用递归方式匹配，所以必须加反斜杠。）。
$ git rm \*~                 # 会递归删除当前目录及其子目录中所有 `~` 结尾的文件。
```

**移动文件**

要在 Git 中对文件改名
```
$ git mv <file> <new file name>
# 上面相当于运行了下面三条命令：
$ mv <file> <new file name>
$ git rm <file>
$ git add <new file name>
```

把当前分支中未提交的修改移动到其他分支：
```
git stash
git checkout branch2
git stash pop
```

 将 stashed changes 应用到当前分支：
```
git stash apply
```

 删除最新一次的 stashed changes：
```
git stash drop
```

![](https://ws3.sinaimg.cn/large/006tKfTcgy1fja82ao6cxj30dw08tgmw.jpg)

------

## 搜索

 从当前目录的所有文件中查找文本内容：

```
$ git grep "Hello"
```

 在某一版本中搜索文本：

```
$ git grep "Hello" v2.5
```

------

## 查看提交历史

```
$ git log          # 显示所有的提交记录（hash， 作者信息，提交时间和说明）
$ git log -p       # 显示每次提交的内容差异
```

 显示reflog：

```
$ git reflog show
```

 删除reflog：

```
$ git reflog delete
```

------

## 分支与标签
**查看分支情况**

```
$ git branch                   # 列出所有的分支（* 字符：表示当前所在的分支）
$ git branch -v                # 查看各个分支最后一个提交对象的信息
$ git branch -r                # 列出所有的远端分支
$ git branch -a                # 查看所有分支(本地+远端)***
$ git branch --merged          # 查看哪些分支已被并入当前分支（即在当前分支的直接上游）
$ git branch --no-merged       # 查看尚未与当前分支合并的分支
```

 **基于当前分支创建新分支**
```
$ git branch <new-branch>
```

 **切换分支**
```
$ git checkout <branch>
```

 **创建并切换到新分支**
```
$ git checkout -b <branch>       # 相当于执行上面两条命令
```

 基于远程分支创建新的可追溯的分支：

```
$ git branch --track <new-branch> <remote-branch>
```

 **删除本地分支**
```
$ git branch -d <branch>            # 未合并的分支会提示错误
$ git branch -D <branch>            # 强制执行，将会丢失未合并的修改！
```

 给当前版本打标签

```bash
$ git log                   # 查看ID 的前 10 位字符
$ git tag <tag-name>        # 如：git tag 1.0.0 1b2e1d63ff
$ git tag -a <tag-name>     # 给当前版本打标签并附加消息
```

------

## 更新与发布

 **列出当前的远程仓库**

```
$ git remote                 # 列出每个远程库的简短名字
$ git remote -v              # 显示对应的克隆地址
$ git remote show <remote>   # 查看远程仓库的信息，如origin

```

 **添加新的远程仓库**

```bash
$ git remote add <remote> <url>   # 指定一个简单的名字(以便将来引用)，指代对应的仓库地址
$ git remote add origin <server>   
# 把远端的「原始来源」设为 github 端点。新增一个远程的仓库，命名为 origin。origin 的位置指向 Github
# 还没有克隆现有仓库，并欲将仓库连接到某个远程服务器，将改动推送到所添加的服务器上去。

```

 下载远程端版本，但不合并到HEAD中：
```
$ git fetch <remote>           # 同步远程服务器上的数据到本地。<remote> 一般为origin   ***
git fetch -p <remote>

```

 下载远程端版本，并自动与HEAD版本合并：
```
$ git remote pull <remote> <url>

```

 将远程端版本合并到本地版本中：
```
$ git pull                                ***拉下远程仓库的变更
$ git pull <remote> <branch>
$ git pull origin master

```

 以rebase方式将远端分支与本地合并：
```
git pull --rebase <remote> <branch>

```

将本地版本发布到远程端：
```
$ git push <remote> <branch>               # 远程仓库名（远端的端点，如：origin）<== 本地分支名
$ git push origin master
$ git push remote <remote> <branch>        #
$ git push remote <remote>:<branch>        # 远程仓库名 远程分支名:本地分支名
$ git push -u origin master                # 预设以后都是推到远程 origin 仓库的 master，所以以后可以直接 git push？
```



 删除远程端分支：
```
$ git push <remote> :<branch> (since Git v1.5.0)
or
git push <remote> --delete <branch> (since Git v1.7.0)

```

 发布标签:
```
$ git push --tags

```

Rename a remote
```
git remote rename <old-name> <new-name>
```

Track a remote repository
```
git remote add --track <remote-branch> <remote> <url>
```

------

## 合并与重置(Rebase)

 将分支合并到当前HEAD中：
```
$ git merge <branch>

```

合并时出现了“Fast forward”的提示。由于当前 master 分支所在的提交对象是要并入的 hotfix 分支的直接上游，Git 只需把 master 分支指针直接右移。换句话说，如果顺着一个分支走下去可以到达另一个分支的话，那么 Git 在合并两者时，只会简单地把指针右移，因为这种单线的历史分支不存在任何需要解决的分歧，所以这种合并过程可以称为快进（Fast forward）。

 将当前HEAD版本重置到分支中:

```
$ git rebase <branch>              # 请勿重置已发布的提交!

```

 退出重置:
```
$ git rebase --abort

```

 解决冲突后继续重置：
```
$ git rebase --continue

```

 使用配置好的merge tool 解决冲突：

```
$ git mergetool

```

 在编辑器中手动解决冲突后，标记文件为`已解决冲突`：

```
$ git add <resolved-file>

```

```
$ git rm <resolved-file>

```

 合并提交：

```
$ git rebase -i <commit-just-before-first>

```

把上面的内容替换为下面的内容：

原内容：

```
pick <commit_id>
pick <commit_id2>
pick <commit_id3>

```

替换为：

```
pick <commit_id>
squash <commit_id2>
squash <commit_id3>

```

------

## 撤销

### commit的删除

```
$ git log                    #  查看现存commit的历史，按q退出
$ git reset --hard HEAD~1    #  数字代表删除多少个分支
$ git reset --hard HEAD      #  放弃工作目录下的所有修改：???

```

 移除缓存区的所有文件（i.e. 撤销上次`git add`）:

```
$ git reset HEAD

```

 放弃某个文件的所有本地修改：

```
$ git checkout HEAD <file>

```

 重置一个提交（通过创建一个截然不同的新提交）

```
$ git revert <commit>

```

### 将HEAD重置到指定的版本，并抛弃该版本之后的所有修改

```
$ git reflog                  # 查看commit历史，包括现存和已删除的，按q退出
$ git reset --hard <commit>   # <commit>为想恢复的commit ID

```

 用远端分支强制覆盖本地分支：

```
git reset --hard <remote/branch> e.g., upstream/master, origin/my-feature

```

 将HEAD重置到上一次提交的版本，并将之后的修改标记为未添加到缓存区的修改：

```
$ git reset <commit>

```

 将HEAD重置到上一次提交的版本，并保留未提交的本地修改：

```
$ git reset --keep <commit>

```

 删除添加`.gitignore`文件前错误提交的文件：

```
$ git rm -r --cached .
$ git add .
$ git commit -m "remove xyz file"

```

**修改的东西不想要保存**

```
$ git status                             # 查看更改了什么
$ git add .                              # 追踪
$ git stash
$ git stash clear
$ git status                             # 继续查看更改了什么（已清空）
```

gitignore

-可以设定哪一些档案不被 git 存取
-比如说 config/database.yml

------

## Reference

[Git Cheat Sheet by iGevin](https://blog.igevin.info/posts/git-cheat-sheet/)
[Git 版本控制系統 —— ihower 的 Git 教室](https://ihower.tw/git/)
[Try Git ⼗五分钟体验](https://try.github.io/levels/1/challenges/1)
[The entire Pro Git book](https://git-scm.com/book)
[Git-recipes](https://github.com/geeeeeeeeek/git-recipes)
[git - 简明指南](http://rogerdudler.github.io/git-guide/index.zh.html)
[Pro git](http://iissnan.com/progit/)
[如何从主项目更新fork的项目？](https://github.com/xugy0926/getting-started-with-javascript/blob/master/topics/%E5%A6%82%E4%BD%95%E4%BB%8E%E4%B8%BB%E9%A1%B9%E7%9B%AE%E6%9B%B4%E6%96%B0fork%E7%9A%84%E9%A1%B9%E7%9B%AE.md)
