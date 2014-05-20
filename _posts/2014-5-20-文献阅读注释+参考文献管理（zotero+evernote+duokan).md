---
layout: post
keywords: evernote, zotero, doukan
description: 文献阅读注释+参考文献管理工具
title: "文献阅读注释+参考文献管理（zotero+evernote+duokan)"
categories: [work]
tags: [reader bibref ]
group: archive
icon: file-alt
---
{% include site/setup %}


文献阅读注释+参考文献管理（zotero+evernote+duokan)
====================================

## duokan:  
最近发现，在手机的5寸屏幕上看书居然是一件很方便的事情，阅读量甚至超过了kindle/pad，实在是因为手机小巧方便携带，在空闲时间里可以随时拿出来，这些不是kindle/pad适合的。找了一圈，从智阅，到kindleReader，最后到duokan多看，结论是多看阅读最方便，对pdf支持功能强（支持重排），自动做笔记注释，阅读进度的同步，还有云空间可以做书籍同步。还有一个关键功能：它支持笔记注释导入evernote。  

## evernote:  
以前用onenote，自从转到ubuntu桌面，也找了一阵子替代软件，结果没有，于是就wine+evernote开始用。当前不久gerry送我一个5寸手机，我才发现原来多设备见的note同步功能这么好，可以随时随地查看笔记，真方便。对我来说，pad还是用得少。
最初，我按类别tag管理笔记，期望把info管理得有条理。比如一门课课件，比如MyinfoBook，比如一个Project。 
接下来，用evernote过程中，逐渐改变了这个习惯。我发现，随任务，记录信息，聚合信息，成为一个更常用的方式。可以说，evernote成为解决一个问题时，记录信息，整理的理想工具。比如这篇笔记的诞生，就是从一个问题开始：我怎么读论文，做笔记，并管理好文件和参考文献，又能在手机/pad上阅读呢？于是，search+read，整个信息搜索，记录，整理的过程都汇聚在evernote的这篇笔记里。等问题解决了，再总结，就是现在敲下的文字~。一个个的微任务，就是我们生活当中一个个信息访问的实际场景，也是信息组织，管理的基本单位。从买菜，出游，购物，读书，写作，研究，各类事务里都有相似的信息访问模式。evernote是一个方便的辅助工具。如果大家都这样用，那么在evernote里记录的笔记们将会是非常有价值的信息，想一想，不得了，弄了半天，web上高质量内容都藏在evernote里面。它们怎么发挥更大的价值？我去另开一个笔记来调研吧。。。。。。    
还得提evernote webclip，这解决了在web 上浏览时保存好信息的需求（虽然保存的内容极少可能会回头再次阅读，但它的确满足了人希望把信息保存下来的需求）。但是为了真正使用这些信息，我觉得，还得回到微任务模式里去——带着问题来阅读，整理，才是有效的。  

## zotero:  
在解决技术问题的调研中，evernote可以帮助记录整理web上的信息，不过稍微深入一点的内容，就涉及到了academic research paper。web内容，简单给一个URL reference或者evernote webclip的link就好，能够访问，但research paper需要链接到PDF file。
管理research paper是件麻烦事。通常，我会按project涉及的问题和领域，建立目录，下载paper保存。但今天调研的问题，涉及到一篇过去曾经看过的paper，也许曾经还对它作过阅读注释，但是现在它在哪？——用文件系统来管理，完全不行。
想到[zotero][1]。好久不用了，一直不写paper，也就不大关心reference。记得很久以前还是用EndNote写了我的毕业论文，那是第一次接触参考文献管理软件，感叹真是好用。后来fankai介绍用了zotero，在firefox里使用，library都在服务器上，不用考虑备份和保存了，很好。现在再一次做'研究', 回到zotero。
[zotero, zandy, greader, evernote and me][2] 提到了zotero和pad之间使用[zotfile][3]论文同步，这正是我想要的。[安装zotfile][8]，在web page上用zotero保存参考条目时，它神奇的自动保存pdf文件/或者监控download目录下新的pdf文件，把它作为附件，并且自动换名，到自己设置的library目录下。文中提到的同步，还得依赖其它pc-mobile之间的同步软件。 我用百度云，于是找到[百度云/百度网盘的Python客户端][7], 试了试，还不错，也算解决了一个长期要换到windows机器上去做云盘同步的麻烦了。虽然，doukan不直接支持百度云盘，但总算打通了这条通道，而我也不需要文中提到的pdf 回传和annotation提取功能，因为duokan可以把它们直接输出到evernote~~~
[Connecting Zotero and Evernote][5] 提到在evernote里，通过[zotero link translator][6] 添加zotero的条目连接，这样就把笔记，注释和zotero library连接起来。

## Summary
现在，有了一个完整的论文阅读，笔记，参考文献管理工具链了： zotero+zotfile -> baiduyun -> duokan reader ->evernote -> zotero. :)


[1]: http://www.zotero.org/ "zotero project"
[2]: http://home.badc.rl.ac.uk/lawrence/blog/2013/09/11/zotero,_zandy,_greader,_evernote,_and_me "zotero, zandy, greader, evernote and me"
[3]: http://zotfile.com/ "zotfile"
[4]: https://play.google.com/store/apps/details?id=com.gimranov.zandy.app&hl=en "zandy"
[5]: http://blog.cdhq.de/archive/1366       "Connecting Zotero and Evernote" 
[6]: http://code.google.com/p/zotero-trans/ "zotero link translator"
[7]: https://github.com/houtianze/bypy "Python client for Baidu Yun 百度云/百度网盘的Python客户端"
[8]: http://www.huangwei.me/blog/2010/02/07/%E5%8E%9F%E5%88%9Bzotero%E7%B3%BB%E5%88%97%E6%95%99%E7%A8%8B%E4%B9%8B%E4%B8%80%E5%9F%BA%E6%9C%AC%E5%8A%9F%E8%83%BD%E5%92%8C%E5%AE%89%E8%A3%85/  "原创zotero系列教程之一基本功能和安装"

