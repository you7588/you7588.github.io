---
title: Terminal Cheatsheet for Mac
date: 2017-09-08 20:20:50
tags: [terminal, cheatsheet]
---

## Terminal(macOS)简介

终端（Terminal，文件名称 Terminal.app），透过这个程式来输入程序指令这里是输入所有指令的地方。在鼠标和图形操作系统诞生前，这种操作方式就存在了。
Terminal 是使用者直接跟「Mac 内核」用「文字沟通」的介面。以往平常作为一个一般用户，我们都是以图形化介面，指挥 Mac 应该要怎么做做事。而开发者，往往更直接高效的，使用文字指令可以复杂的与 Mac 用文字指令沟通更多事。

<!--more-->
## 快捷键  
> [符号具体详见此处](https://you7588.github.io/2017/09/05/markdown/)

指令    	          |             描述
    ---             |             ---
⇥ 	                |            自动补全文件或文件夹的名称
⌃ P	                |            调出历史中的前一条（Previous）命令，相当于↑
⌃ N	                |            调出历史中的下一条（Next）命令，相当于↓
⌃ R	                |            检索使用过的命令
⌃ A	                |            光标移动到行首（Ahead of line），相当于Home键
⌃ E	                |            移光标移动到行尾（End of line），相当于End键
⌃ T	                |            将光标前的两个文字进行互换
⎋ T	                |            将光标前的两个单词进行互换  
⌃ Y	                |            粘贴最后一次被删除的单词
⌃ W	                |            删除光标之前的单词
⌃ K	                |            删除光标后的所有文字
⌃ U	                |            删除光标前的所有文字
⌃ L	或 ⌘ K          |            清屏，相当于执行`clear`命令
  |  
⌃ C	                |            终止当前执行
⌃ D	                |            退出当前shell
⌃ Z	                |            将执行中任何东西放入后台进程,`fg`可将其恢复
  |  
~~⌃ F~~             |            ~~光标向前移动一个单词~~
~~⌃ B~~	            |            ~~光标向后移动一个单词~~
~~⌃ H~~             |            ~~与退格键相同~~


## 核心命令

指令    	                   |                描述
---                          |                ---
`cd`或`cd ~`	                |                切换到Home目录
`cd /`	                     |                切换到根目录
`cd [folder]`	               |                切换目录
`ls`	                       |                列出当前目录下所有的档案
`ls -al`	                   |                详细列出当前目录下所有档案的信息  
`ls -l`	                     |                文件详细列表
`ls -lh`	                   |                文件详细列表中的文件大小以更友好的形式列出
`ls -a`	                     |                列出隐藏文件夹
`ls -R`	                     |                递归显示文件夹中的内容
`sudo [command]`	           |                以超级用户身份执行命令
`open [file]`	               |                打开文件 ( 相当于双击一个文件 )
`open.`	                     |                打开当前文件
`top`	                       |                显示运行中的进程，按q终止
~~`nano [file]`或`pico	[file]`~~	  |            ~~打开编辑~~
`q`		                       |                退出
`clear`		                   |                清屏

## 命令历史

指令    	                  |                描述
---                        |                ---
`history n`	               |                列出最近执行过的n条命令,n可以指任何数字
`![value]`	               |                执行最近以'value'开始的命令
`!!`	                     |                执行最近执行过的命令



## 文件管理

指令    	                     |               描述
---                            |               ---
`touch [file]`	               |               创建一个新文件
`pwd`	                         |               显示当前工作目录
`..`	                         |               上级目录
`ls -l ..`                     |               上级目录的文件详细列表
`cd ../../`                    |               向上移动两个层级     
~~`cat`~~		                   |               ~~连接?~~
`rm [file]`	                   |               移除文件/目录
`rm -i [file]`	               |               移除时出现确认提示
`rm -r [dir]`	                 |               移除文件及内容
`rm -f [file]`	               |               强制移除
`cp [file] [newfile]`          |               复制文件/目录
`cp [file] [dir]`	             |               复制文件到指定目录
`mv [file] [new filename]`     |               移动/修改文件名或目录, 如`mv -v [file] [dir]`



## 目录管理
> 使用命令行工具，可以对系统下的文件（file）和目录（folder/dirctory/dir，这三个词在大多数情况下是一回事）

指令    	                         |        描述
---                                |        ---
`mkdir [dir]`	                     |        创建新目录
`mkdir -p [dir]/[dir]`             |        创建子目录
`rmdir [dir]`                      |        移除目录 ( 仅限目录下没有内容时 )
`rm -rf [dir]`                     |        强制删除
`mvdir [dir1] [dir2]`              |        移动或重命名一个目录
`rm -R [dir]`                      |        移除目录及内容


## 管道 - 连接多个带有输出的命令
>不太懂

指令    	                         |        描述
---                               |        ---
more	                            |        按当前窗口大小输出内容
> [file]	                        |        输出至指定文件, 注意文件将会覆盖
>> [file]	                        |        在制定文件的末尾附加内容
<	                                |        从文件中读取内容


## 帮助
>没试过

指令    	                         |        描述
---                               |        ---
[command] -h	                    |        显示帮助信息
[command] --help	                |        显示帮助信息
[command] help	                  |        显示帮助信息
reset	                            |        重置当前终端
man [command]	                    |        显示指定命令的帮助信息
whatis [command]	                |        显示指定命令的简述


## 参考

[wiki-Terminal_(macOS)](https://en.wikipedia.org/wiki/Terminal_(macOS))
[Terminal Cheatsheet for Mac ( 基本 )](https://github.com/0nn0/terminal-mac-cheatsheet/tree/master/%E4%B8%AD%E6%96%87%E8%AF%B7%E5%8F%82%E8%80%83)
