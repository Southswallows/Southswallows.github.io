---
layout: post
category: 读书
title: Mac Talk 随记
tags: Mac
---


####用AppleScript实现一个示例小功能

	tell application "Finder"		set isEmpty to "是否清空废纸篓！"		display dialog isEmpty		empty the trash		say "It is done!"	end tell
	
####poadcast推荐

- English as a Second Language
####Homebrew
**Mac OSX上的软件包管理工具**Homebrew的功能和OS X自带的MacPorts很像，但是更为轻量级，由于大量利用了系统自带的库，安装方便，编译快速，实在是OS X系统开发中之必备工具。

安装方式：
	
	ruby -e “$(curl -fsSkL raw.github.com/mxcl/homebrew/go)”
最新的：

	ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

使用方式：
	
	brew install wget //安装wget工具。

具体的使用请参考：
	
	https://github.com/mxcl/homebrew/wiki
	
卸载软件：

	brew uninstall wget

####QuickTime

- option+command+n，可以打开录像功能
- ctrl+option+command+n可以打开录音功能
- ctrl+command+n可以打开录制屏幕功能

**在文件菜单中找到这三项。**

####Autojump

**安装**

	brew install autojump
**配置**

	nano .zshrc
	找到plugins=() 这行
	添加 autojump 记得各插件名之间用英文空格隔开
	例如 plugins=(git autojump)

####小技巧

- fn+delete可以往前删除
- fn+上下左右方向键可以实现PageUP/PageDown/Home/End的功能
- 当选择要保存的文件路径时，我们可以提前打开要保存的Finder窗口，在选择保存的窗口时，通过**command+r**直接打开Finder，Finder会自动跳到你选择的路径，完成保存操作后切换到这个Finder窗口即可。
- 在launch界面，按住option键 可以使图标抖动
- mdls:列出某个文件或文件夹的所有元数据信息.

		例子：mdls ~/Desktop/a.jpg
- file和mdls差不多 比较亲民
- 废纸篓删除不掉时：

		sudo rm -rf ~/.Trash/
- 打开OS X的终端，通过man命令可以直接查看该命令的使用手册，在终端输入如下命令，即可在预览程序打开grep的使用手册，另存为你需要的文件名

		man -t grep | open -f -a Preview
- 使非视网膜的app，变成视网膜的app[retinizer](http://retinizer.mikelpr.com/)
- 对于单个文件的比较，一般使用diff或vimdiff就可以了，比如：

		vimdiff destfile.txt sourcefile.txt