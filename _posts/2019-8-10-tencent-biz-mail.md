---
layout: post
title: '打造腾讯企业邮专属邮箱登录页'
date: 2019-08-10
cover: 'http://pic.jj20.com/up/allimg/1011/110916134009/161109134009-1.jpg'
tags: 实验
---

腾讯企业邮箱专业版有个功能叫登录模板,复制HTML代码就可以放到自己的网页上了,默认是长这样的...

![1.png](https://s2.ax1x.com/2019/08/10/eXkghQ.png)

是不是有点复古呢,不过没有关系!让我们观察一下鹅厂的这段代码吧

```
    <style>
    .bizmail_loginpanel{font-size:12px;width:300px;height:auto;border:1px solid #cccccc;background:#ffffff;}
    .bizmail_LoginBox{padding:10px 15px;}
    .bizmail_loginpanel h3{padding-bottom:5px;margin:0 0 5px 0;border-bottom:1px solid #cccccc;font-size:14px;}
    .bizmail_loginpanel form{margin:0;padding:0;}
    .bizmail_loginpanel input.text{font-size:12px;width:100px;height:20px;margin:0 2px;border:1px solid #C3C3C3;border-color:#7C7C7C #C3C3C3 #C3C3C3 #9A9A9A;}
    .bizmail_loginpanel .bizmail_column{height:28px;}
    .bizmail_loginpanel .bizmail_column label{display:block;float:left;width:30px;height:24px;line-height:24px;font-size:12px;}
    .bizmail_loginpanel .bizmail_column .bizmail_inputArea{float:left;width:240px;}
    .bizmail_loginpanel .bizmail_column span{font-size:12px;word-wrap:break-word;margin-left: 2px;line-height:200%;}
    .bizmail_loginpanel .bizmail_SubmitArea{margin-left:30px;clear:both;}
    .bizmail_loginpanel .bizmail_SubmitArea a{font-size:12px;margin-left:5px;}
    .bizmail_loginpanel select{width:110px;height:20px;margin:0 2px;}
    </style>
    <script type="text/javascript" src="http://exmail.qq.com/zh_CN/htmledition/js_biz/outerlogin.js"  charset="gb18030"></script>
    <script type="text/javascript">
    writeLoginPanel({domainlist:"sherry.cf", mode:"vertical"});
    </script>
```

可以看出样式是可以自己进行修改的,而让登录邮箱发挥作用的是script标签中的`writeLoginPanel({domainlist:"sherry.cf", mode:"vertical"});`,将domainlist的值修改为你绑定的腾讯企业邮域名就行了了

只换换样式好像有点单调呀?让我们继续观察...这段代码还引用了一个js文件,那这个js文件的作用是什么呢?

怀着这样的疑问我打开了http://exmail.qq.com/zh_CN/htmledition/js_biz/outerlogin.js ,发现这里面也是有HTML代码的!

```
var e='return checkInput()',c='<div id="divLoginpanelHor" class="bizmail_loginpanel" style="width:550px;"><div class="bizmail_LoginBox"><h3>\u767B\u5F55\u90AE\u7BB1</h3><form name="form1" action="https://exmail.qq.com/cgi-bin/login" target="_blank" method="post" onsubmit="'+e+'"><input type="hidden" name="firstlogin" value="false" /><input type="hidden" name="errtemplate" value="dm_loginpage" /><input type="hidden" name="aliastype" value="other" /><input type="hidden" name="dmtype" value="bizmail" /><input type="hidden" name="p" value="" /><label>\u5E10\u53F7:</label><input type="text" name="uin" class="text" value="" />@#domainlist#<label>&nbsp;\u5BC6\u7801:</label><input type="password" name="pwd" class="text" value="" /><input type="submit" class="" name="" value="\u767B\u5F55" />&nbsp;<a href="https://exmail.qq.com/cgi-bin/readtemplate?check=false&t=biz_rf_portal#recovery" target="_blank">\u5FD8\u8BB0\u5BC6\u7801\uFF1F</a></form></div></div>',d='<div id="divLoginpanelVer" class="bizmail_loginpanel"><div class="bizmail_LoginBox"><h3>\u767B\u5F55\u90AE\u7BB1</h3><form name="form1" action="https://exmail.qq.com/cgi-bin/login" target="_blank" method="post" onsubmit="'+e+'"><input type="hidden" name="firstlogin" value="false" /><input type="hidden" name="errtemplate" value="dm_loginpage" /><input type="hidden" name="aliastype" value="other" /><input type="hidden" name="dmtype" value="bizmail" /><input type="hidden" name="p" value="" /><div class="bizmail_column"><label>\u5E10\u53F7:</label><div class="bizmail_inputArea"><input type="text" name="uin" class="text" value="" />@#domainlist#</div></div><div class="bizmail_column"><label>\u5BC6\u7801:</label><div class="bizmail_inputArea"><input type="password" name="pwd" class="text" value="" /></div></div><div class="bizmail_SubmitArea"><input type="submit" class="" name="" style="width:66px;" value="\u767B\u5F55" /><a href="https://exmail.qq.com/cgi-bin/readtemplate?check=false&t=biz_rf_portal#recovery" target="_blank">\u5FD8\u8BB0\u5BC6\u7801\uFF1F</a></div></form></div></div>';
```

这行代码就是登录模板上文字的来源,如果你想添加点图标或者是更改文字也是没问题的

这时候我们先将js文件保存,再把中文转换为Unicode,并替换掉label标签中的Unicode,再把js文件放到网页的同级别目录里

加上渐变色背景,看看效果如何?

![1.png](https://s2.ax1x.com/2019/08/10/eXm6A0.md.png)

哇,太棒了,我们终于完成了一个自定义邮箱登录页~
