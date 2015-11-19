---
layout: post
category: 科研
title: 给Eclipse安装CDT插件
tags: 喉镜
---

##给Eclipse安装CDT插件
-----

###【背景】

需要用到CDT插件，所以要去给Eclipse安装CDT插件。

###【解决过程】

1. 用Eclipse的自带的那个查找和安装的功能去安装CDT。

2. Eclipse->Help->Install New Software

	![eclipse-help-install-new-software](http://7xkeeu.com1.z0.glb.clouddn.com/eclipse-help-install-new-software_thumb.png)

3. Work With中，选择当前Eclipse版本的那个地址：

		Juno – http://download.eclipse.org/releases/juno

然后搜索CDT，然后就可以看到搜出来的CDT了：

		Autotools support for CDT 
		CDT Visual C++ Support
		
![choose-juno-input-cdt-choose-cdt](http://7xkeeu.com1.z0.glb.clouddn.com/choose-juno-input-cdt-choose-cdt_thumb.png)
		
4. 下一步后，可以看到详细信息：

		Autotools support for CDT    3.0.1.201302132326    org.eclipse.cdt.autotools.feature.group 
		Plugins for maintaining C/C++ projects that use Autotools (autoconf and automake).
  		CDT Visual C++ Support    1.0.0.201302132326    org.eclipse.cdt.msw.feature.group 
		Support for building project using the Visual C++ compiler.
		
![install-details-for-cdt](http://7xkeeu.com1.z0.glb.clouddn.com/install-details-for-cdt_thumb.png)
		
5. 接受条款：

![cdt-agree-license](http://7xkeeu.com1.z0.glb.clouddn.com/cdt-agree-license_thumb.png)


6. 然后就是去下载和安装了：

![installing-software-for-cdt](http://7xkeeu.com1.z0.glb.clouddn.com/installing-software-for-cdt_thumb.png)


7. 安装完CDT后需要重启Eclipse

![install-cdt-complete-need-reboot](http://7xkeeu.com1.z0.glb.clouddn.com/install-cdt-complete-need-reboot_thumb.png)

8. 重启后，去：

Window->Preferences

![eclipse-window-preferences](http://7xkeeu.com1.z0.glb.clouddn.com/eclipse-window-preferences_thumb1.png)

中确认已经安装成功：

可以看到C/C++了：

![](http://7xkeeu.com1.z0.glb.clouddn.com/eclipse-support-c-cpp-now_thumb.png)


###【总结】

其实就是：

	Eclipse->Help->Install New Software->

Work With选择：
		
	Juno – http://download.eclipse.org/releases/juno

输入CDT，然后选择找到的那两个：

		Autotools support for CDT    3.0.1.201302132326    org.eclipse.cdt.autotools.feature.group 
		CDT Visual C++ Support    1.0.0.201302132326    org.eclipse.cdt.msw.feature.group
		
一路安装即可。