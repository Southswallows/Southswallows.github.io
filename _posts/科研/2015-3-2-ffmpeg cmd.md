---
layout: post
category: 科研
title: FFmpeg命令行
tags: 喉镜
---


- 截取一张352x240尺寸大小的，格式为jpg的图片

		ffmpeg -i test.asf -y -f image2 -t 0.001 -s 352x240 a.jpg  
		test.asf--源文件
		a.jpg---生成的文件
- 把视频的前30帧转换成一个Animated Gif 

		ffmpeg -i test.asf -vframes 30 -y -f gif a.gif
- 截取指定时间的缩微图,-ss后跟的时间单位为秒

		ffmpeg -i test.avi -y -f image2 -ss 8 -t 0.001 -s 350x240 test.jpg
		第八秒之后的图片截取出来





[参考网页](http://www.oschina.net/code/snippet_222150_25379)
