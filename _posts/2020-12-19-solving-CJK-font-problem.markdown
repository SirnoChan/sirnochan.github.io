---
layout: post
title: "用Stylish插件修复pixiv等网站中日韩字体混乱的问题"
time: 2020-12-19 16:33:10
---
pixiv等网站为了美观，强制将汉字字体指定为Meiryo体，于是在浏览中文内容的时候会出现有的大陆特有、Meiryo体里面没有的简化字与其他汉字字体不统一的情况。解决方法之一是使用Stylish以及CSS的新特性[@font-face](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@font-face)自定义本地字体文件，比如思源系字体。以下是不完善的补救措施示例：

```CSS
    @font-face {

        font-family: Meiryo;

        src: local(Noto Sans CJK JP Light), local(Noto Sans CJK JP Light);

    }
```
