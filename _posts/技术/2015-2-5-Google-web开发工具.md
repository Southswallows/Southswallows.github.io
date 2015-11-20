---
layout: post
category: 技术
title: Chrome web开发工具
tags: web
---
-   Google Chrome一共提供了8大组工具
      1. Elements: 允许我们从浏览器的角度看页面，也就是说我们可以看到chrome渲染页面所需要的的HTML、CSS和DOM(Document Object Model)对象。此外，还可以编辑这些内容更改页面显示效果；
      2. Network: 可以看到页面向服务器请求了哪些资源、资源的大小以及加载资源花费的时间，当然也能看到哪些资源不能成功加载。此外，还可以查看HTTP的请求头，返回内容等
      3. Sources: 主要用来调试js；
      4. Timeline: 提供了加载页面时花费时间的完整分析，所有事件，从下载资源到处理Javascript，计算CSS样式等花费的时间都展示在Timeline中；
      5. Profiles: 分析web应用或者页面的执行时间以及内存使用情况；
      6. Resources: 对本地缓存（IndexedDB、Web SQL、Cookie、应用程序缓存、Web Storage）中的数据进行确认及编辑；
      7. Audits: 分析页面加载的过程，进而提供减少页面加载时间、提升响应速度的方案；
      8. Console: 显示各种警告与错误信息，并且提供了shell用来和文档、开发者工具交互。
- 选中标签之后，右击出现的操作项：
      1. Add Attribute: 在标签中增加新的属性；
      2. Force Element State: 有时候我们为页面元素添加一些动态的样式，比如当鼠标悬停在元素上时的样式，这种动态样式很难调试。我们可以使用Force Element State强制元素状态，便于调试
      3. Edit as HTML: 以HTML形式更改页面元素；
      4. Copy XPath: 复制XPath；
      5. Delete: 删除DOM节点；
      6. Break On: 设置DOM 断点。
- CSS样式、属性等，一共有以下5小部分：
      1. Style:显示用户定义的样式，比如请求的default.css中的样式，和通过Javasript生成的样式，还有开发者工具添加的样式；
      2. Computed: 显示开发者工具计算好的元素样式；（现在没有咯）
      3. Event Listeners: 显示当前HTML DOM节点和其祖先节点的所有JavaScript事件监听器，这里的监听脚本可以来自Chrome的插件。可以点击右边小漏斗形状(filter)选择只显示当前节点的事件监听器。
      4. Breakpoints: 列出所有的DOM 断点；
      5. Properties: 超级全面地列出当前选中内容的属性，不过基本很少用到。
- 当网页加载很慢的时候，可以通过network工具进行查看加载速度慢的原因  
- 每个资源在Network表格中显示为一行，相关参数说明：
    1. Name/Path: 资源名称以及URL路径； 
    2. Method: HTTP请求方法；
    3. Status/Text: HTTP状态码/文字解释；
    4. Type: 请求资源的MIME类型；
    5. Initiator解释请求是怎么发起的，有四种可能的值：
        1. Parser：请求是由页面的HTML解析时发送的；
        2. Redirect：请求是由页面重定向发送的；
        3. Script：请求是由script脚本处理发送的；
        4. Other：请求是由其他过程发送的，比如页面里的link链接点击，在地址栏输入URL地址。
    6. Size/Content: Size是响应头部和响应体结合起来的大小，Content是请求内容解码后的大小。进一步了解可以看这里Chrome Dev Tools - “Size” vs “Content”；
    7. Time/Latency: Time是从请求开始到接收到最后一个字节的总时长，Latency是从请求开始到接收到第一个字节的时间；
    8. Timeline: 显示网络请求的可视化瀑布流，鼠标悬停在某一个时间线上，可以显示整个请求各部分花费的时间。
- Network上部6个功能：
    1. Record Network Log: 红色表示此时正在记录资源请求信息；
    2. Clear: 清空所有的资源请求信息
    3. Filter: 过滤资源请求信息；
    4. Use small resource raws: 每一行显示更少的内容；
    5. Perserve Log: 再次记录请求的信息时不擦出之前的资源信息；
    6. Disable cache: 不允许缓存的话，所有资源均重新加载。
- 点击资源后产生另个列表的说明：
    1. HTTP request and response headers
    2. Resource preview: 可行时进行资源预览；
    3. HTTP response: 未处理过的资源内容；
    4. Cookie names and values: HTTP请求以及返回中传输的所有Cookies；
    5. WebSocket messages: 通过WebSocket发送和接收到的信息；
    6. Resource network timing: 图形化显示资源加载过程中各阶段花费的时间。