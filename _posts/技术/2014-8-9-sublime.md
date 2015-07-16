---
layout: post
category: 技术
title: Sublime text2
tags: Mac
---

![sublime](http://7xkeeu.com1.z0.glb.clouddn.com/23976426eacc47b0c67ff44c752aab02.jpg)
#####在mac的命令行中打开sublime方式
- 软链接的方式：在命令行中输入下面代码

		 ln -s /Applications/Sublime\ Text\ 2.app/Contents/SharedSupport/bin/subl /usr/local/bin/subl
`本机为osx10.10，sublime text2`
- 命令行操作

		ublime Text 2 Build 2221

		Usage: subl [arguments] [files]         edit the given files 编辑所给的文件
 	    or: subl [arguments] [directories]      open the given directories 打开所给的文件夹
  		or: subl [arguments] -                  edit stdin 

		Arguments:
  		--project <project>: Load the given project 加在所给的工程
  		--command <command>: Run the given command  运行所给的命令
  		-n or --new-window:  Open a new window 打开新的窗口
 		-a or --add:         Add folders to the current window 在当前窗口中添加文件夹
  		-w or --wait:        Wait for the files to be closed before returning 
  		-b or --background:  Don't activate the application 在后台运行
  		-s or --stay:        Keep the application activated after closing the file  当关闭文件之后程序还运行
  		-h or --help:        Show help (this message) and exit 
  		-v or --version:     Show version and exit
  		
  		
###Sublime text2 使用技巧

**可以在sublime界面上通过preferences>key binding**中查看

- ctrl+~  打开命令行
- **Shift + ctrl + P**调出命令面板
- 安装软件是调出命令面板之后，输入install package  再后面弹出的窗口中搜索需要的package
- 自动补全的快捷键**tab**
- **ctrl+/、ctrl+shift+/**分别未行**注释**和块注释，再按一下就能去掉注释
- **重新打开刚关闭**的标签页：**cmd + shift + t**
-** 括号前后移动**光标：**ctrl + m **
- **Ctrl+G：***跳转* 到第几行
- **Ctrl+W：**关闭当前打开文件
- **Ctrl+Shift+W：**关闭所有打开文件
- **Ctrl+Shift+V：**粘贴并格式化
- **Ctrl+D：**选择单词，重复可增加选择下一个相同的单词
- **Ctrl+L：**选择行，重复可依次增加选择下一行
- **Ctrl+Shift+L：**选择多行
- **Ctrl+Shift+Enter：**在当前行前插入新行
- **Ctrl+X**：删除当前行
- **Ctrl+U：**软撤销，撤销光标位置
- **Ctrl+J：**选择标签内容
- **Ctrl+Shift+F：**查找并替换
- **Ctrl+H：**替换
- **Ctrl+R：**前往 method
- **Ctrl+N：**新建窗口
- **Ctrl+Shift+M：**选中当前括号内容，重复可选着括号本身
- **Alt+数字**：切换打开第N个文件
- **sidebar**  打开侧栏

-----
####打开和前往

- ⌘T	前往文件
- ⌘⌃P	前往项目
- ⌘R	前往 method
- ⌘⇧P	命令提示
- ⌃G	前往行
- ⌘KB	开关侧栏
- ⌃ `	python 控制台
- ⌘⇧N	新建窗口

####编辑

- ⌘L	选择行 (重复按下将下一行加入选择)
- **⌘D**	选择词 (重复按下时多重选择相同的词进行多重编辑)
- ⌃⇧M	选择括号内的内容
- ⌘⇧↩	在当前行前插入新行
- ⌘↩	在当前行后插入新行
- ⌃⇧K	删除行
- ⌘KK	从光标处删除至行尾
- ⌘K⌫	从光标处删除至行首
- ⌘⇧D	复制(多)行
- ⌘J	合并(多)行
- ⌘KU	改为大写
- ⌘KL	改为小写
- ⌘ /	注释
- ⌘⌥ /	块注释
- ⌘Y	恢复或重复
- ⌘⇧V	粘贴并自动缩进
- ⌃ space	自动完成(重复按下选择下一个提示)
- ⌃M	跳转至对应的括号
- ⌘U	软撤销（可撤销光标移动）
- ⌘⇧U	软重做（可重做光标移动）

####查找和替换

- ⌘F	查找
- ⌘⌥F	替换
- ⌘⌥G	查找下一个符合当前所选的内容
- ⌘⌃G	查找所有符合当前所选的内容进行多重编辑
- ⌘⇧F	在所有打开的文件中进行查找



-----
- 选中多行+`Tab`：整体缩进
- `Shift`+`Tab`:整体取消缩进
- 按下`Command+Shift+L`即可同时编辑这些行；
- 鼠标选中文本，反复按`Command+D`即可继续向下同时选中下一个相同的文本进行**同时编辑**
- 鼠标选中文本，按下`Alt+F3 (Win)`或`Ctrl+Command+G(Mac)`即可一次性选择全部的相同文本进行同时编辑；
- `Shift+鼠标右键(Win)`或`Option+鼠标左键(Mac)`或使用鼠标中键可以用鼠标进行竖向多行选择
- `Ctrl+鼠标左键(Win)`或`Command+鼠标左键(Mac)`可以手动选择同时要编辑的多处文本
- Shift+Command+P(Mac) 即可调出文件切换面板
- Shift+Command+P(Mac)，这次试试先输入一个 @,罗列出这文件里全部的 Function

-----

####随心所欲跳转
1. 用 **Command+P** 可以快速跳转到当前项目中的任意文件，可进行关键词匹配。
2. 用 **Command+P 后 @** (或是**Command+R**)可以快速列出/跳转到某个函数（很爽的是在 markdown 当中是匹配到标题，而且还是带缩进的！）。
3. 用 **Command+P 后 #** 可以在当前文件中进行搜索。
4. 用 **Command+P 后 : (或是Ctrl+G)**加上数字可以跳转到相应的行。
5. 而更酷的是你可以用 Command+P 加上一些关键词跳转到某个文件同时加上 @ 来列出/跳转到目标文件中的某个函数，或是同时加上 # 来在目标文件中进行搜索，或是同时加上 : 和数字来跳转到目标文件中相应的行。

------------
###推荐使用的插件：

- emmet   
- allautocompltete   （搜索所有打开的文件，进行关键词提示）
- sublimerepl   （在编辑器中运行各种语言）
- color highlighter (展示你所选择的颜色代码)
- autofilename  (自动补全文件路径)
- colorcoder
