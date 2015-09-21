---
layout: post
category: life
title: 机械键盘初体验＋karabiner使用
tags: 
---

###Filco minila 67 AIR

早已经垂涎机械键盘很久了，在同学从日本回国之际，立马代购入手这款键盘`Filco minila 67 AIR(青轴)`
![keyboard](http://7xkeeu.com1.z0.glb.clouddn.com/keyboard.jpg)
在机械键盘轴的选取过程中，产生了纠结，在茶，红，青中做决定。

- 茶轴－－－最中庸的一款，有机械的手感，最接近于薄膜键盘，声音大小适中。
- 红轴－－－相对于其他轴稍微贵一点，手感不错，声音小很多，办公室不会一直啪啪啪。
- 青轴－－－最能让你感受机械键盘手感的，那点按的分层次的感觉加上啪啪啪的声音，让你又爱又恨。但是键程较长，打时间长会有点累。

**犹豫再三，选择了买青轴，就爱那和打字机一样的声音**

**键盘的功能不在这边多说，网上开箱一大把**

**下面说说怎么改键，满足MAC的使用**



###神器karabiner

![karabiner](http://7xkeeu.com1.z0.glb.clouddn.com/KEY.png)

可以通过官网下载，[地址](https://pqrs.org/osx/karabiner/)

下载安装大方法和一半的mac软件一样，不再赘述。

###设置键的功能

官方的使用方法也比较的详细，对着步骤，很容易的完成操作。

- **[官方使用教程-1](https://pqrs.org/osx/karabiner/document.html.en)**

- **[官方使用教程-2](https://pqrs.org/osx/karabiner/xml.html.ja)**

###个性化设置

- 打开`karabiner`,在**preferencces**---**Misc & Uninstall**中点击**Open private.xml**，会弹出来一个文档。打开该文档.
- 语法的基本操作
		
		<item>
		<name>Hyper+space To Enter</name>  <!--显示在karabiner选项里的名字-->
		<appendix>Hyper(cmd+ctrl+shift+opt)+space, send enter</appendix> <!--显示在karabiner选项里的说明-->
		<identifier>private.hyperspace2enter</identifier>  <!--唯一性的标识符-->
		<autogen>
		--KeyToKey--
		KeyCode::SPACE,  <!--快捷键第一项-->
		ModifierFlag::OPTION_L | ModifierFlag::SHIFT_L | 
		KeyCode::ENTER  <!--映射后的结果-->
		</autogen>
		</item>
		
###MAC设置实例

####最后达成的效果：

1. 左边的command和option键交换位置（`为了和笔记本上相同`）
2. F1,F2，F5～F12和mac键盘上对应的功能的相同
3. 使用右`option`键来切换输入法
4. F3， F4键来截图(F3保存截图，F4截图至剪切版)

```

<?xml version="1.0"?>
<root>
<!--command和option键交换位置 -->
	<item>
    <name>[FILCO_MINILA] cmd change to option</name>
    <identifier>private.cmdtooption</identifier>
    <autogen>__KeyToKey__ KeyCode::OPTION_L, KeyCode::COMMAND_L</autogen>
    <autogen>__KeyToKey__ KeyCode::COMMAND_L, KeyCode::OPTION_L</autogen>
  </item>
<!-- 使用F1,F2，F5～F12原来mac键盘上的功能-->
  <item>
    <name>Function Keys</name>
    <appendix>F1～F2，F7～F12</appendix>
    <identifier>remap.volumeKeys</identifier>
    <autogen>__KeyToKey__ KeyCode::F1,  ConsumerKeyCode::BRIGHTNESS_DOWN</autogen>  
    <autogen>__KeyToKey__ KeyCode::F2,  ConsumerKeyCode::BRIGHTNESS_UP</autogen>  
    <autogen>__KeyToKey__ KeyCode::F7,  ConsumerKeyCode::MUSIC_PREV</autogen>  
    <autogen>__KeyToKey__ KeyCode::F8,  ConsumerKeyCode::MUSIC_PLAY</autogen>  
    <autogen>__KeyToKey__ KeyCode::F9,  ConsumerKeyCode::MUSIC_NEXT</autogen>  
    <autogen>__KeyToKey__ KeyCode::F10, ConsumerKeyCode::VOLUME_MUTE</autogen>  
    <autogen>__KeyToKey__ KeyCode::F11, ConsumerKeyCode::VOLUME_DOWN</autogen>  
    <autogen>__KeyToKey__ KeyCode::F12, ConsumerKeyCode::VOLUME_UP</autogen>  
  </item>
<!-- 使用右option键来切换输入法 -->
  <item>
    <name>Switch Input Source</name>
    <identifier>private.remap.input_source</identifier>
    <autogen>__KeyToKey__ 
    KeyCode::OPTION_R, 
    KeyCode::SPACE, ModifierFlag::COMMAND_L,
    </autogen>
  </item>
<!--F3， F4键来截图(保存截图，不保存截图)-->
  <item>
    <name>Catch Screen</name>
    <identifier>private.remap.catch_screen</identifier>
    <autogen>__KeyToKey__ 
    KeyCode::F3, 
    KeyCode::KEY_4, ModifierFlag::SHIFT_L | ModifierFlag::COMMAND_L,
    </autogen>  
    <autogen>__KeyToKey__ 
    KeyCode::F4,  
    KeyCode::KEY_4, ModifierFlag::SHIFT_L | ModifierFlag::CONTROL_L | ModifierFlag::COMMAND_L,
    </autogen> 
  </item>
</root>

```
