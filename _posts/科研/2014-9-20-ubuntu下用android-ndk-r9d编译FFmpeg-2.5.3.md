---
layout: post
category: 科研
title: ubuntu下用android-ndk-r9d编译FFmpeg-2.5.3
tags: 喉镜
---





##ubuntu下用android-ndk-r9d编译FFmpeg-2.5.3


###[参考内容](http://www.roman10.net/how-to-build-ffmpeg-with-ndk-r9/)

1. 下载最新版本的Android NDK文件

	[点击下载NDK文件](http://developer.android.com/tools/sdk/ndk/index.html)
	写文章的时候，最新版本的NDK是`android-ndk-r9d`
	
	`注意：`不同版本的NDK编译方法可能会有不一样的地方
	
	下载完成之后，进行解压，解压后存储在`NDK文件夹下`
	
2. 下载最新的ffmpeg源文件

	[点击下载ffmpeg](http://www.ffmpeg.org/download.html)
	
	写文章时候，最新版本是`FFmpeg-2.5.3`
	
	下载解压之后，将文件放在`NDK文件夹`下
	
3. 修改配置文件（`configure文件`）

	使用文本编辑器打开**`FFmpeg-2.5.3/configure`**
	
	找到下面的代码段
	
		SLIBNAME_WITH_MAJOR='$(SLIBNAME).$(LIBMAJOR)'
		LIB_INSTALL_EXTRA_CMD='$$(RANLIB) "$(LIBDIR)/$(LIBNAME)"'
		SLIB_INSTALL_NAME='$(SLIBNAME_WITH_VERSION)'
		SLIB_INSTALL_LINKS='$(SLIBNAME_WITH_MAJOR) $(SLIBNAME)'
		
	这些代码段，将`ffmpeg`的共享库编译为libavcodec.so文件，但是没有使用Android编译系统，因此我们需要将上面代码段替换为下面的代码段
	
		SLIBNAME_WITH_MAJOR='$(SLIBPREF)$(FULLNAME)-$(LIBMAJOR)$(SLIBSUF)'
		LIB_INSTALL_EXTRA_CMD='$$(RANLIB) "$(LIBDIR)/$(LIBNAME)"'
		SLIB_INSTALL_NAME='$(SLIBNAME_WITH_MAJOR)'
		SLIB_INSTALL_LINKS='$(SLIBNAME)'
4. 开始编译`ffmpeg`

	新建build_android.sh.脚本，复制粘贴下面内容
	
		#!/bin/bash
		NDK=$HOME/Downloads/ndk/android-ndk-r10d
		SYSROOT=$NDK/platforms/android-9/arch-arm/
		TOOLCHAIN=$NDK/toolchains/arm-linux-androideabi-4.8/prebuilt/linux-x86
		function build_one
		{
		./configure \
   			 --prefix=$PREFIX \
    		 --enable-shared \
           --disable-static \
           --disable-doc \
           --disable-ffmpeg \
           --disable-ffplay \
           --disable-ffprobe \
           --disable-ffserver \
           --disable-avdevice \
           --disable-doc \
           --disable-symver \
           --cross-prefix=$TOOLCHAIN/bin/arm-linux-androideabi- \
           --target-os=linux \
           --arch=arm \
           --enable-cross-compile \
           --sysroot=$SYSROOT \
           --extra-cflags="-Os -fpic $ADDI_CFLAGS" \
           --extra-ldflags="$ADDI_LDFLAGS" \
           $ADDITIONAL_CONFIGURE_FLAG
     	make clean
		make
		make install
		}
		CPU=arm
		PREFIX=$(pwd)/android/$CPU 
		ADDI_CFLAGS="-marm"
		build_one
	上面的脚本没有针对特定的CPU，可以参考ffmpeg文件进行具体的设置
	
	保存好文件之后，在终端中输入下面代码，将文件转换为可执行文件
		
		sudo chmod +x build_android.sh
	然后执行下面的命令
	
		./build_android.sh
		
5. 编译输出的文件

	编译将进行一段时间，这根据你电脑的硬件情况而定。一旦编译完毕，你可以在`$NDK/sources/ffmpeg-2.5.3/android`文件夹下包含`arm/lib`和`arm/include `文件夹
	
	`arm/lib`文件夹内包含共享库
	
	`arm/lib`文件夹内包含libavcodec, libavformat, libavfilter, libavutil, libswscale等的头文件
	
	`arm/lib`文件夹内包含库的名字如libavcodec-56.so....

6. 使你编译好的ffmpeg库文件能运用于自己的项目

	Android NDK允许我们再利用编译模块通过使用导入模块的命令行
	
	使ffmpeg库文件作为重复使用的模块，新建Android.mk文件，如下：
	
		LOCAL_PATH := $(callmy-dir)  
   
		include $(CLEAR_VARS)  
		LOCAL_MODULE :=avcodec-56-prebuilt  
		LOCAL_SRC_FILES :=prebuilt/libavcodec-56.so  
		include$(PREBUILT_SHARED_LIBRARY)  
    
   
		include $(CLEAR_VARS)  
		LOCAL_MODULE :=avfilter-5-prebuilt  
		LOCAL_SRC_FILES :=prebuilt/libavfilter-5.so  
		include$(PREBUILT_SHARED_LIBRARY)  
   
		include $(CLEAR_VARS)  
		LOCAL_MODULE :=avformat-56-prebuilt  
		LOCAL_SRC_FILES :=prebuilt/libavformat-56.so  
		include$(PREBUILT_SHARED_LIBRARY)  
   
		include $(CLEAR_VARS)  
		LOCAL_MODULE :=  avutil-54-prebuilt  
		LOCAL_SRC_FILES :=prebuilt/libavutil-54.so  
		include$(PREBUILT_SHARED_LIBRARY)  
   
		include $(CLEAR_VARS)  
		LOCAL_MODULE :=  avswresample-1-prebuilt  
		LOCAL_SRC_FILES :=prebuilt/libswresample-1.so  
		include $(PREBUILT_SHARED_LIBRARY)  
   
		include $(CLEAR_VARS)  
		LOCAL_MODULE :=  swscale-3-prebuilt  
		LOCAL_SRC_FILES :=prebuilt/libswscale-3.so  
		include$(PREBUILT_SHARED_LIBRARY)  
   
		include $(CLEAR_VARS)  
   
		LOCAL_MODULE :=ffmpeg_codec  
		LOCAL_SRC_FILES :=cn_dennishucd_FFmpegNative.c  
   
		LOCAL_LDLIBS := -llog-ljnigraphics -lz -landroid  
		LOCAL_SHARED_LIBRARIES:= avcodec-56-prebuilt avfilter-5-prebuilt avformat-56-prebuilt avutil-54-prebuilt  
   
		include$(BUILD_SHARED_LIBRARY)  
		
	有些相应的部分需要进行修改，如：**LOCAL_SRC_FILES :=prebuilt/libswscale-3.so**的数字什么的，要和自己的文件相对应。
	
	文件保存到**$NDK/sources/ffmpeg-2.0.1/android/arm/**
