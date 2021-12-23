---
layout: post
title: "Windows下更改FireFox的默认字体的字重，以及将Emoji换为其他样式"
time: 2021-12-23 15:52:27
---

虽然在最近的更新中（大约是93.0）中FireFox移除了菜单栏中自由选择网页编码的选项，FireFox在设置中仍允许用户对给定语言设定自定义的默认字体。如果用户没有取消勾选「`允许页面选择自己的字体代替您的上述选择(A)`」的话，这一功能只用于网站未给定字体的情况。但这里有一个不足之处是无法修改字体的字重。

为什么我要修改字体的字重？因为我想把字体改成思源宋体。而宋体的一大特点是在同一字重下，感官上比黑体要细，这样子更加剧了与黑体相比的屏显上的劣势，主要表现就是更难看清笔画。而将字体的字重增加可以多少缓解这个问题。一般情况下，FireFox的默认字重为400，对应的是字体的Regular，黑体的Regular要比宋体粗一点，所以宋体要把字重调高一级到500，即Medium。但是思源宋体在不同字重下，横向笔画的粗细似乎是固定的。这就意味着即使改了字重，始终会有看不清的笔画。

![思源宋体示例]({{Site.url}}/assets/SerifCJKDemo-1.png "思源宋体示例图一")
![思源宋体示例]({{Site.url}}/assets/SerifCJKDemo-2.png "思源宋体示例图二")

FireFox在设置中没有给出具体的不同字重的字体的选项。于是我第一个想到的是像上次一样用Stylish改字体，但是FireFox的字体设置不会改变CSS，而是直接在渲染时动手脚，Stylish也不能利用@fontface对引用的字体做手脚。所以更现实的方法是在FireFox的`About:Config`里直接改动引用的字体文件。思源宋体的字体文件对应多个字重，想用哪个字重的话可以直接指定字体文件。

在`about:config`中搜索`font`，会发现一长串键。需要改的键有：
* `font.name.sans-serif.zh-CN`
* `font.name.sans-serif.zh-HK`
* `font.name.sans-serif.zh-TW`

把它们改成思源宋体的字体名，后面用空格隔开加上`Medium`，就是Medium字重对应的字体名了。

这样改了之后，更细的字体无法显示，更粗的字体仍然用Medium字重渲染。问题很多……可能直接用方正悠宋这种杂交了黑体的字体的效果会更好。

----

在改字体的过程中，我还发现一个叫`font.name-list.emoji`的键，其值为`Segoe UI Emoji, Twemoji Mozilla`，前者是Windows自带的Emoji字体，后者是Mozilla根据Twitter开放的资源做的字体，应该是FireFox内置的。如果我们把之前的Segoe UI Emoji删掉，网页上的字体就会变成Twitter风格的字体，比Windows的要好看多了。如此，若在系统中安装了旧版Google Emoji字体的，应该也可以把Emoji换成果冻人。

![在浏览器中查看更改后的字体]({{Site.url}}/assets/ModifiedWebEmoji.png "修改为Twitter样式的字体")