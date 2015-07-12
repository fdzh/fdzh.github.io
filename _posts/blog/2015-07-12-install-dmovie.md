---
layout: post
author: 1dot75cm
category: blog
title: Fedora22 安装深度影音
tags: Fedora22 deepin-movie
image: http://repo.fdzh.org/img/snapshot3.jpg
---

经过不断的调试，今天终于成功将 Deepin Movie 迁移至 Fedora 21/22。~\(≧▽≦)/~

深度一直是国内开源界的良心企业，Linux Deepin 系统包含的一系列本土化的应用也给 Linux 桌面带来了全新的操作体验。

本次迁移的 [深度影院 v2.2.2](http://planet.linuxdeepin.com/freely-play-with-ultimate-fluency-deepin-movie-v2-2-enjoy-your-audio-visual-feast) 采用全新的 [QtAV](http://www.qtav.org) 多媒体框架，极大增强了解码能力，可流畅播放各类高清视频。

4K.2160p.120fps 测试视频：http://pan.baidu.com/s/1sjykTqt

Fedora 21/22 添加 [FZUG](http://repo.fdzh.org) 社区源后，执行以下命令：

{% highlight bash %}
{% raw  %}
# dnf install deepin-movie
{% endraw  %}
{% endhighlight %}
