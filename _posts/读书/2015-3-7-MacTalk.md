---
layout: post
category: 读书
title: MacTalk 读书笔记
tags: Mac
---

####软件推荐：

- SecureCRT－－－串口调试工具
- iunarchive/the unarchiver 压缩软件
- breeze 窗口管理的软件
- Go2shell  在浏览的文件目录中打开终端进行
		
		下载完成之后，将应用程序拖到Finder工具栏上，随便进入目录之后点击go2shell图标，就可以在终端中显示
		通过 open -a Go2Shell --args config  进入配置界面
- remote desktop connection to mac  在mac中通过远程界面连接windows
- Flux 调节屏幕色温


####使用技巧using skills

- 使用sips命令批量处理图片
		
		sips －z 800 ~/Pictures/*.jpg   //将图片宽度缩小为800px 图片高度按比例缩放
		sips -r 90 ~Pictures/*.jpg    //将图片顺时针旋转90度
		sips －f vertical ～Pictures/*.jpg  //将图片垂直翻转
		详见 sips －h

- 在safari中 在网页中使用`command＋i`可以讲此网页已邮件方式进行发送。
- 在终端中实现查看文件夹的大小

		du -sh *
		du -- display disk usage statistics
		
- 执行维护脚本
	
		sudo periodic daily weekly mouthly  
		
- 显示目前系统的进程情况 
		
		输入top
		然后输入？ 会显示帮助信息
- 批量复制移动文件

		cp *.jpg *.png *.gif /destpath
		mv *.jpg *.png *.gif /destpath
- 显示历史命令
		
		终端下输入history 
		历史命令对应一个唯一的编号
		使用！1000  即再次执行原来的命令

- safari阅读器，在app下点击图标或者使用`shift+command+r`进入阅读器模式，下载扩展程序customreader进行自定义化阅读界面。
- 选中文字按`shift+command+y` 打开便签并添加文字
- open可打开文件、文件夹、应用程序、使用指定应用程序打开文件、打开网址
	
		open -a safari
		open -a TextMate a.txt
		open http://.......
- 拖拽其他窗口的时候按住`commad`就可以是当前窗口一直在最前面。
- 离开电脑一段时间 但是电脑不休眠，在终端使用 

		pmset noidle
		关闭终端就结束啦

- 复制目录下多有文件的列表`command+a``command+c`打开文本编辑器`command+v`即可
- 重建spotlight（当运行缓慢时执行）

		sudo mdutil -i off /
		sudo mdutil -E /
		sudo mdutil -on /
		
- 禁止通知：按住option＋通知图标
- 硬链接

		ln xxx  xxx
- 软链接

		ln -s xxx xxx

	
		