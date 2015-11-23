---
layout: post
author: tvvocold
category: blog
title: Fedora 安装搜狗输入法
tags: Fedora sougoupinyin
image: http://7xi3zv.com1.z0.glb.clouddn.com/556130f783d0f25.png_600x600.png
---

经过开发和测试同学的辛勤劳动，搜狗输入法 For Linux 近日发布了 [2.0.0.0066](http://pinyin.sogou.com/linux/changelog.php) 更新： 

新增双拼支持；
修复少数情况下焦点跳动问题；
改进部分桌面环境兼容性；
修复新建覆盖词库不生效问题；
调整tab切换界面控件顺序。

下面我们在 Fedora 22 上安装搜狗输入法。

1, 安装 Fedora 中文社区软件源
{% highlight bash %}
{% raw  %}
$ sudo dnf config-manager --add-repo=http://repo.fdzh.org/FZUG/FZUG.repo 
$ sudo dnf install fzug-release -y
{% endraw  %}
{% endhighlight %}

2, 安装搜狗拼音输入法 Linux 版

{% highlight bash %}
{% raw  %}
$ sudo dnf install sogoupinyin sogoupinyin-selinux -y
{% endraw  %}
{% endhighlight %}

3, 重启

{% highlight bash %}
{% raw  %}
$ reboot
{% endraw  %}
{% endhighlight %}


感谢 [1dot75cm](http://cm.fdzh.org) 为 [Fedora中文社区软件源](http://repo.fdzh.org) 打包了该软件。
