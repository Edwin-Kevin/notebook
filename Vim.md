# Vim 的三种模式

1. 正常模式
2. 编辑模式
3. 命令行模式

# 导航

正常模式下，HJKL， 分别代表←↓↑→

# 编辑

i： 在光标前插入编辑（insert 插入）

a： 在光标后插入编辑（append 追加）

I： 在行首插入编辑

A： 在行尾编辑

o： 新起一行编辑（open a new line）

O： 在上方新起一行编辑

G： 将光标移动到最后一行

gg： 到第一行

> *~/.vimrc* 中添加 `set number` 可以为 vim 编辑器加入行号。

5j： 向下移动5行

5k： 向上移动5行

> 配置文件添加 `set relativennumber` 开启相对行号模式。

:20： 跳转到第20行

yy： 复制当前行（yank）

p： 粘贴

dd： 剪切当前行

. ： 重复前次操作

u： 撤销前次操作（undo）

Ctrl + r： 重做前次操作

dw： 删除单词（delete word）

cw： 更改单词（change word）

w： 下一个单词首部

e： 下一个单词尾部

b： 上一个单词首部

# 搜索、替换与视觉模式

`/<string>` ： 搜索字符串

`:%s/<old>/<new>/g` ： g代表global，全局替换；

`yw` : 复制一个单词

`3p` ： 执行三次粘贴

`ci{` 或 `ci}`： 删除 `{}` 中的内容

`Ctrl + v` ：可视化块

`Shift + v` ： 可视化行

> 可视化选中后，按 `d` 删除

