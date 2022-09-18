# VIM

Vi 编辑器是所有 Unix 及 Linux 系统下标准的编辑器，在 Unix 及 Linux 系统的任何版本，Vi 编辑器是完全相同的，Vi 也是 Linux 中最基本的文本编辑器。

vim 编辑器是在 vi 的基础上改进的版本，比 vi 功能更强大，支持语法颜色，是 vi 的升级版。

# 模式

Vim 中存在三种模式：**命令模式、编辑模式（输入模式）、末行模式（尾行模式）**。

- 命令模式：在该模式下不能对文件直接编辑，可以通过快捷键进行一些操作（复制行，移动光标等），打开文件之后默认进入的模式
- 编辑模式：在该模式下可以对文件的内容进行编辑
- 末行模式：可以在末行输入命令来对文件进行操作（搜索、替换、保存、退出、撤销、高亮等等）

模式之间的切换：

- 命令模式：打开文件默认该模式，其他模式通过 `esc` 返回该模式
- 末行模式：在命令模式通过 `:` 进入
- 编辑模式：在命令模式通过 `i`、`a` 等进入

模式间的切换必须通过**命令模式**间接切换。

# 打开文件

1. `vim 路径`：打开指定文件
2. `vim +数字 路径`：打开指定文件，并将光标移动到指定的行
3. `vim +/关键词 路径`：打开指定的文件，并且高亮显示关键词
4. `vim 路径1 路径2 路径3`：同时打开多个文件

# 命令模式

> 该模式是打开文件直接进入的模式

## 光标移动

1. 光标移动到**行首**：`shift + 6` === `^`
2. 光标移动到**行末**：`shift + 4` === `$`
3. 光标移动到**首行**：`gg`
4. 光标移动到**末行**：`G`
5. 翻屏操作
	- 向上翻屏：`ctrl + b`
	- 向下翻屏：`ctrl + f`
6. 移动到指定的行：`数字G `
7. 向上/向下移动n行：`n↑` / `n↓`
8. 向左/向右移动n字符：`n←` / `n→`
9. **末行模式**下移动到指定的行：`:n`

## 复制操作

1. 复制光标所在行：`yy`
2. 以光标所在行开始，向下复制指定的行数：`数字yy`
3. 可视化复制：通过 `ctrl v` / `V` / `v` 进行可视化选中，`y` 进行复制

粘贴使用 `p` 键，如果复制的是整行，粘贴都是粘贴到选中位置的下一行。

## 剪切/删除

1. 剪切/删除光标所在行：`dd`
2. 以当前行开始，向下删除/剪切指定的行：`数字dd`
3. 剪切/删除光标所在的当前行之后的内容，但是删除之后下一行不上移：`D`
4. 可视化删除/剪切：通过 `ctrl v` / `V` / `v` 进行可视化选中，按下 `D` 表示删除**选中行**，`d` 表示删**选中块**

## 撤销/恢复

- 撤销：`:u`，属于末行模式
- 恢复：`ctrl + r`

# 末行模式

进入方式：在命令模式通过 `:` 进入，或者通过 `/` 查找进入

## 退出模式

- `esc`
- 两次 `esc`
- 删除末行全部字符

## 保存和退出

1. 保存操作：`:w`
2. 另存为：`:w 路径`
3. 退出：`:q`
4. 保存并退出：`wq`，`:x`，后一个如果没有修改就是 `:q`，文件修改了就是 `:wq`
5. 强制操作：`q!` 表示强制退出
6. 调用外部命令：`!命令`

## 查找

- 查找：`/关键词`
	- 在搜索结果中切换上/下一个结果：N/n
	- 取消高亮，则需要输入：`:nohl`
- 查找并替换内容
	- `:s/搜索的关键词/新的内容`：替换光标所在行的第一处符合条件的内容
	- `:s/搜索的关键词/新的内容/g`：替换光标所在行的全部符合条件的内容
	- `:%s/搜索的关键词/新的内容`：替换整个文档中每行第一个符合条件的内容
	- `:%s/搜索的关键词/新的内容/g`:替换整个文档的符合条件的内容

## 其他

- 显示行号：`:set nu`
- 取消显示行号：`set nonu`

- 查看已经打开的文件：`:files`
- 切换文件：
	- `:open 文件名`：切换到已经打开的其他文件
	- `:bn`：切换到下一个文件
	- `:bp`：切换到上一个文件
- 控制代码着色：
	- `:syntax on`
	- `:syntax off`
- 分屏操作：
	- 垂直分屏：`:vs [file]`
	- 水平分屏：`:sv [file]`
	- 移动当前屏幕：`ctrl ww`
	- 关闭当前屏幕：`:hide`、`ctrl w c`
	- 将当前屏移动到最左 / 右端：`ctrl w H`、`ctrl w L`
	- 将当前屏移动到最上 / 下端：`ctrl w K`、`ctrl w J`

# 编辑模式

## 进入方式

- `i`：在光标字符前插入
- `a`：在光标字符后插入
- `o`：在光标所在行的另起新一行插入
- `I`：在光标所在行的行首开始插入，如果行首有空格则在空格之后插入
- `A`：在光标所在行的行尾插入
- `O`：在光标所在行的上面另起一行插入
- `S`：删除光标坐在行并开始插入

## 计算器

当在编辑文件的时候突然需要使用计算器去计算一些公式，则此时需要用计算器，vim自身集成了一个简易的计算器。

在编辑模式：

1. 按下 `ctrl + R`
2. 输入 `=` 
3. 输入需要计算的内容，按下回车
4. 结果会被输入到光标所在位置

# 配置文件

Vim配置有三种情况：

- 在文件打开的时候在末行模式下输入的配置（临时的）
- 个人配置文件（`~/.vimrc`，如果没有可以自行新建）
- 全局配置文件（vim自带，`/etc/vimrc`）

# 异常退出

在编辑文件之后并没有正常的去保存退出，而是遇到突然关闭终端或者断电的情况，则发生了异常退出。

解决办法：

- `:recover` 进行恢复
- `rm -f .passwd.swp` 删除交换文件


