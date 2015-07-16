---
layout: post
category: 读书
title: learn python the hard way
tags: python
---

- %---表示求余
- %r 不论什么都答应出来 包括符号‘’等
- from sys import argv和raw_input差不多的
- argv是所谓的“参数变量(argument variable)”，在运行python时要进行变量赋值。变量值就赋值给相应的变量了。
- script, first, second, third = argv
- return－－－将值返回给函数，在函数里面使用
- 将一串字符串按单词打散，使用.split
- 对单词进行排序，使用sort(存储字符串的变量)
- 提取一串字符串中的第一个单词.pop(0)  最后一个单词.pop(-1)
- 导入python文件作为模块import ...不需要写xxx.py。这样可以直接调用里面的函数。
- 帮助文档就是你定义函数时放在 """  """之间的东西，它们也被称作 documentation comments （文档注解）
- “类即是对象”的概念。他们决定用小写的“object”这个词作为一个类，让你在创建新类时从它继承下来。一个类从另一个类继承，而后者虽然是个类，但名字却叫“object”在定义类的时候，别忘记要从object继承。
- **Python的class永远都要求你加上(object)** 