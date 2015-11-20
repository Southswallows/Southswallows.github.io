---
layout: post
category: 科研
title: Android-Universal-Image-Loader库使用
tags: 喉镜
---

###[Github主页](https://github.com/nostra13/Android-Universal-Image-Loader)

###Android-Universal-Image-Loader是一款开源的图片异步加载类库

----
**简单描述一下这个项目的结构：每一个图片的加载和显示任务都运行在独立的线程中，除非这个图片缓存在内存中，这种情况下图片会立即显示。如果需要的图片缓存在本地，他们会开启一个独立的线程队列。如果在缓存中没有正确的图片，任务线程会从线程池中获取，因此，快速显示缓存图片时不会有明显的障碍。**

1. 多线程下载图片，图片可以来源于网络，文件系统，项目文件夹assets中以及drawable中
2. 支持随意的配置ImageLoader，例如线程池，图片下载器，内存缓存策略，硬盘缓存策略，
3. 片显示选项以及其他的一些配置
4. 支持图片的内存缓存，文件系统缓存或者SD卡缓存
5. 支持图片下载过程的监听
6. 根据控件(ImageView)的大小对Bitmap进行裁剪，减少Bitmap占用过多的内存
7. 较好的控制图片的加载过程，例如暂停图片加载，重新开始加载图片，一般使用
8. ListView,GridView中，滑动过程中暂停加载图片，停止滑动的时候去加载图片
9. 提供在较慢的网络下对图片进行加载

###配置参数

		ImageLoaderConfiguration config = new ImageLoaderConfiguration.Builder(context)
        .memoryCacheExtraOptions(480, 800) // default = device screen dimensions 内存缓存文件的最大长宽
        .diskCacheExtraOptions(480, 800, null)  // 本地缓存的详细信息(缓存的最大长宽)，最好不要设置这个 
        .taskExecutor(...)
        .taskExecutorForCachedImages(...)
        .threadPoolSize(3) // default  线程池内加载的数量
        .threadPriority(Thread.NORM_PRIORITY - 2) // default 设置当前线程的优先级
        .tasksProcessingOrder(QueueProcessingType.FIFO) // default
        .denyCacheImageMultipleSizesInMemory()
        .memoryCache(new LruMemoryCache(2 * 1024 * 1024)) //可以通过自己的内存缓存实现  内存缓存
        .memoryCacheSize(2 * 1024 * 1024)  // 内存缓存的最大值
        .memoryCacheSizePercentage(13) // default
        .diskCache(new UnlimitedDiscCache(cacheDir)) // default 可以自定义缓存路径
        .diskCacheSize(50 * 1024 * 1024) // 50 Mb sd卡(本地)缓存的最大值
        .diskCacheFileCount(100)  // 可以缓存的文件数量 
        // default为使用HASHCODE对UIL进行加密命名， 还可以用MD5(new Md5FileNameGenerator())加密
        .diskCacheFileNameGenerator(new HashCodeFileNameGenerator()) 
        .imageDownloader(new BaseImageDownloader(context)) // default
        .imageDecoder(new BaseImageDecoder()) // default
        .defaultDisplayImageOptions(DisplayImageOptions.createSimple()) // default
        .writeDebugLogs() // 打印debug log
        .build(); //开始构建

###相关显示参数配置

		DisplayImageOptions options = new DisplayImageOptions.Builder()
        options = new DisplayImageOptions.Builder()  
		 .showImageOnLoading(R.drawable.ic_launcher) //设置图片在下载期间显示的图片  
		 .showImageForEmptyUri(R.drawable.ic_launcher)//设置图片Uri为空或是错误的时候显示的图片  
		.showImageOnFail(R.drawable.ic_launcher)  //设置图片加载/解码过程中错误时候显示的图片
		.cacheInMemory(true)//设置下载的图片是否缓存在内存中  
		.cacheOnDisc(true)//设置下载的图片是否缓存在SD卡中  
		.considerExifParams(true)  //是否考虑JPEG图像EXIF参数（旋转，翻转）
		.imageScaleType(ImageScaleType.EXACTLY_STRETCHED)//设置图片以如何的编码方式显示  
		.bitmapConfig(Bitmap.Config.RGB_565)//设置图片的解码类型//  
		.decodingOptions(android.graphics.BitmapFactory.Options decodingOptions)//设置图片的解码配置  
		//.delayBeforeLoading(int delayInMillis)//int delayInMillis为你设置的下载前的延迟时间
		//设置图片加入缓存前，对bitmap进行设置  
		//.preProcessor(BitmapProcessor preProcessor)  
		.resetViewBeforeLoading(true)//设置图片在下载前是否重置，复位  
		.displayer(new RoundedBitmapDisplayer(20))//是否设置为圆角，弧度为多少  
		.displayer(new FadeInBitmapDisplayer(100))//是否图片加载好后渐入的动画时间  
		.build();//构建完成  

------
		
		  以上配置中的：
	 1）.imageScaleType(ImageScaleType imageScaleType)  是设置 图片的缩放方式
     缩放类型mageScaleType:

              EXACTLY :图像将完全按比例缩小的目标大小

              EXACTLY_STRETCHED:图片会缩放到目标大小完全

              IN_SAMPLE_INT:图像将被二次采样的整数倍

              IN_SAMPLE_POWER_OF_2:图片将降低2倍，直到下一减少步骤，使图像更小的目标大小

              NONE:图片不会调整
 	 2）.displayer(BitmapDisplayer displayer)   是设置 图片的显示方式

      显示方式displayer：

              RoundedBitmapDisplayer（int roundPixels）设置圆角图片

              FakeBitmapDisplayer（）这个类什么都没做

              FadeInBitmapDisplayer（int durationMillis）设置图片渐显的时间
			  SimpleBitmapDisplayer()正常显示一张图片　