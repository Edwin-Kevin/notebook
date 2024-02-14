# 什么是Git?
是一个版本控制系统，保存每一个版本的文件，并且能实现多人协作下的差异合并

集中式版本控制系统：SVN,所有的文件保存在中央服务器上，电脑保存副本  
分布式版本控制系统：Git（使用最广泛）

# Git的配置
配置用户名

    git config --global user.name [username]

省略（Local）：只针对本地仓库有效  
--global 代表对所有仓库有效（常用）  
--system 代表对所有用户有效

配置邮箱

    git config --global user.email [email]

# 新建仓库
创建仓库的两种方式

## 本地创建新仓库

Method 1: 首先要在本地创建新的文件夹，并在文件夹内部操作

    git init

Method 2: 直接输入要创建的文件夹名

    git init [repo name]


## 从远程克隆一个已有仓库

    git clone [remote link]

# 工作区域和文件状态
Git的本地数据管理分为三个区域：
- 工作区(.git所在目录)
- 暂存区(.git/index)
- 本地仓库(.git/objects)

工作区-->git add-->暂存区-->git commit--->本地仓库

---

git中文件的状态：
- 未跟踪（新添加，未被Git管理的文件）
- 未修改（已被Git管理，但文件内容没有发生变化）
- 已暂存（文件已修改，未进入暂存区）
- 已提交

# 添加和提交文件

    git init               创建仓库
    git status             查看仓库状态
    git add                添加到暂存区（支持通配符）
    git commit             提交（仅提交暂存区中的文件）
    git log [--oneline]    查看提交记录
    git ls-files           查看已被暂存的文件

# 回退版本

## git reset的三种模式（默认为--mixed）

|模式|保留工作区|保留暂存区|
|----|----|----|
|git reset --soft|√|√|
|git reset --hard|×|×|
|git reset --mixed|√|×|

---
    
## 查看操作历史记录
    
    git reflog

# 查看差异

git diff:  

查看文件在工作区、暂存区和版本库之间的差异（默认是查看工作区和暂存区之间的差异，后加HEAD为比较工作区与版本库之间差异，后加--cached为比较暂存区与版本库之间的差异）  

也可以查看文件在两个特定版本之间的差异（后面加上两个commit的提交ID），后面如果再跟文件名，则只查看这个文件在这两个版本之间的差异  

以及查看不同分支之间的差异

---
HEAD代表当前分支的最新提交

HEAD~或HEAD^代表上一次提交

HEAD~2代表前两个版本，以此类推

# 删除文件

## 方法一

先删除本地的文件，然后使用git add [deleted filename]

注意：git add指的是把文件记录更新到暂存区，而不是把文件添加到暂存区

---

## 方法二

    git rm [filename]

此命令可以同时删除工作区和暂存区的文件

    git rm --cached [file]     从暂存区中删除，但保留在工作区
    git rm  -r *               递归删除

删除后记得提交

# 忽略文件

## 应该忽略哪些文件?

- 系统或软件自动生成的文件
- 编译产生的中间文件和可执行文件
- 运行时生成的临时文件
- 涉及到敏感信息的文件

## 文件规则

首先创建 `.gitignore` 文件，然后在里面写入要忽略的文件名，也可以使用通配符;  
文件夹则为`directory name/`。

P.S：忽略操作对已经添加进版本库中的文件无效，空文件夹默认被忽略。

- `#` 一般用作注释
- 规则列表从上到下，逐个读取
- 采用Glob模式进行匹配：

    - `*` 通配任意个字符
    - `?` 匹配单个字符
    - 中括号代表匹配列表中的单个字符，比如[abc]表示a/b/c

- `**` 表示匹配任意的中间目录
- 中括号可以使用 `-` 进行连接，比如：

    - [0-9] 表示任意一位数字
    - [a-z] 表示任意一位小写字母

- `!` 代表取反

[常见语言的.gitignore文件模板](https://github.com/github/gitignore)

# 远程仓库

    git pull    从远程仓库拉取到本地
    git push    从本地推送到远程仓库

如果是本地新建的仓库，没有与远程仓库关联，则需要先关联;  
如果一开始是clone的远程仓库，可以直接推拉。

# 本地仓库和远程仓库关联

    git remote add <shortname> <url>

`<shortname>` 是在git本地指定的，用来为远程仓库设置的别名。

    git remote -v

这是为了查看远程仓库设定情况

    git branch -M main                              指定分支的名字为main
    git push -u origin main                         向origin的远程仓库推送main分支
    git push -u origin master:main                  把本地的master分支推送到远程main分支
    git pull origin <remote branch>:<local branch>  
    
`git pull` 会拉取远程更改并自动合并，而 `git fetch` 只会拉取，不会自动合并。

# 分支

代码中的不同版本，可以独立存在，且有自己的提交记录。

    git branch                                  查看当前仓库中的所有分支
    git branch <branch name>                    创建新分支
    git switch <branch name>                    切换分支
    git merge <slave-branch> <main-branch>      合并分支
    git branch -d <branch name>                 删除分支（未合并前不能删）
    git branch -D <branch name>                 强行删除
    