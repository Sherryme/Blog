---
layout: post
title: '记一次不想写检讨的应对措施'
date: 2019-11-15
cover: 'https://s2.ax1x.com/2019/11/15/Mac32q.jpg'
tags: 实验
---

昨天晚自习之前，我和同学们在玩手机，期间有人起哄，我没有在意。

此时，突然辅导员进来了，质问我们为什么不交手机，纪律委员为什么不点名，于是我们就被罚写一千字检讨了……

怎么办呢，我好冤枉，我又没有起哄啊，上课之前玩手机错了吗？

这时候我突然想起之前知乎看到的用word命令行莽出手写体的教程，于是我做了这些事：

1.百度1000字检讨书

2.打开word，粘贴并修改文章

3.调整word页边距

4.下载手写体（此处使用【嵐】芊柔体）

5.开启word宏命令

步骤：文件-选项-信任中心-信任中心设置-启用所有宏

6.运行宏命令（代码如下）
```
Sub 字体修改()
'
' 字体修改 宏
'
'
Dim R_Character As Range

Dim FontSize(5)
'指定五种字号
FontSize(1) = "16"
FontSize(2) = "16.2"
FontSize(3) = "16.5"
FontSize(4) = "17"
FontSize(5) = "17.2"

Dim ParagraphSpace(5)
'指定五种行间距
ParagraphSpace(1) = "12"
ParagraphSpace(2) = "13"
ParagraphSpace(3) = "17"
ParagraphSpace(4) = "9"
ParagraphSpace(5) = "12"

For Each R_Character In ActiveDocument.Characters
    VBA.Randomize
'字号在5种指定大小中随机选取
    R_Character.Font.Size = FontSize(Int(VBA.Rnd * 5) + 1)
'位置在1—3之间随机选取
    R_Character.Font.Position = Int(VBA.Rnd * 3) + 1
    R_Character.Font.Spacing = 0

Next
Application.ScreenUpdating = True

For Each Cur_Paragraph In ActiveDocument.Paragraphs
'行间距在5个指定值中随机选取
    Cur_Paragraph.LineSpacing = ParagraphSpace(Int(VBA.Rnd * 5) + 1)
    
Next
    Application.ScreenUpdating = True
    
End Sub
```
7.加上红色下划线、稿纸字样

8.保存为pdf方便打印

完成，最后亮成品：
![检讨书.jpg](https://s2.ax1x.com/2019/11/15/Mac32q.jpg)

打印之后成功糊弄了室友和班长，从此写检讨书都一劳永逸啦~

代码参考：
[https://zhuanlan.zhihu.com/p/63921449](https://zhuanlan.zhihu.com/p/63921449) -如何用Word宏命令莽出手写效果(知乎-koko可可)
