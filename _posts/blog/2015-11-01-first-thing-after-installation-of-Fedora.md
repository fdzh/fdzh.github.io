---
layout: post
author: 1dot75cm
category: blog
title: Fedora 安装后需要做的第一件事
tags: Fedora SELinux
image: http://7xi3zv.com1.z0.glb.clouddn.com/126b382.jpg
---

一直以来，Red Hat 系的许多教程，都会建议你关闭 SELinux。确实，启用 SELinux 可能会造成许多莫名其妙的错误。但在实际生产环境，甚至是用户工作站，Red Hat 都建议将 SELinux 设为 enforcing 模式，因为它在关键时候可以成为你系统安全的最后一道防线。

## 程序是不可信的

技术的发展日新月异，我们的系统安全却不容乐观。[wooyun.org](http://www.wooyun.org) 时不时爆出的各种漏洞，都在提醒我们 *程序总是存在缺陷的*。

传统的操作系统采用 DAC 机制，它针对用户进行访问控制，系统会信任用户执行的所有程序，但往往用户**无法判断**程序是否存在安全问题。

后来，出现了 MAC 机制，它以进程为访问控制的首要目标，通过规则严格限制程序运行时可以执行的系统调用。

另外，在保密级别较高的地方，根据资源的机密程度结合 MAC 又衍生出了 MLS 多级安全策略。

我们的主角 SELinux 是 MAC+MLS 的实现方案之一，它最初由 NSA 基于 flask 框架开发，目前主要由 Tresys 和 Red Hat 进行维护。

## 用户与隐私

自 1987 年 9 月 20 日，CANET 向世界发出第一封 E-mail 为标志，互联网正式进入中国大陆。截至 2015 年 6 月，我国网民已达到 6.68 亿人。随着网络的发展，隐私与安全一直是大受关注的话题。现在，随便什么应用/网站都需要注册，各种客户端都提供网络连接功能。在不知不觉中，你的联系人，朋友圈都展示在了网上。可以负责任的说，在互联网面前，我们每个人都没有隐私。

保护个人隐私是一个系统工程。它需要可信的硬件/固件，可信的操作系统，可信的应用程序，可信的网络环境，可信的用户。

- 硬件方面：X86、Arm 体系就是事实的工业标准，但目前没有可信的第三方机构进行评估。
- 系统方面：尽量使用开源操作系统，Open Source 可以确保系统没有恶意行为。
  - 早在 1985 年，美国国防部公布了 [可信计算机系统评估标准](http://csrc.nist.gov/publications/history/dod85.pdf)，该标准将计算机系统分为 A(A1), B(B3 B2 B1), C(C2 C1), D(D1) 四个等级，共7个级别。没有 SELinux 的 Linux 和 Windows 一样都处于 C2 级别。
- 应用程序：尽量使用开源软件，闭源软件或多或少都会侵犯用户隐私。
- 网络方面：尽量不访问/注册来历不明的网站，尽量不使用公共 Wifi。事实上，个人无法控制运营商的行为。
- 用户方面：用户对于隐私保护有最重要的作用。俗话说得好，“机器是死的，人是活的“。只有用户养成了良好的习惯，才能保护好隐私。切勿抱有”**我的信息并没有什么卵用**“的侥幸心理。

## SELinux 与隐私保护

SELinux 为系统提供了额外的一层保护，能够在一定程度上防止隐私泄露。这里提一下基本概念， SELinux 是基于标签的强制访问控制系统。所有系统资源都包含标签上下文，只有进程标签符合访问对象（文件/socket/dbus...）的标签，才允许进程访问该资源。而标签又关联了一系列角色（role），角色又关联了一系列 SELinux user。通过将 SELinux user 与 Linux user 关联，该用户就具有了这些标签。此时，用户执行的程序就都处于这些标签规则的限制范围了。

在 Fedora 中，默认用户关联 unconfined_t 标签，该标签是无限制的，相当于未启用 SELinux。这主要为了兼容性考虑，targeted 规则仅限制网络相关应用。Red Hat 建议用户关联非 unconfined_t 标签来提高安全性。

1. 配置账户映射 SELinux user

{% highlight bash %}
{% raw  %}
$ sudo semanage login -a -s staff_u -r s0:c0.c1023 Jone
{% endraw  %}
{% endhighlight %}

2. 配置 sudo，指定需要转换的 ROLE/TYPE

{% highlight bash %}
{% raw  %}
$ sudo echo "Jone ALL=(ALL) TYPE=unconfined_t ROLE=unconfined_r ALL" >> /etc/sudoers.d/Jone
{% endraw  %}
{% endhighlight %}

3. 对 home 目录重新进行标记，并重启

{% highlight bash %}
{% raw  %}
$ restorecon -R -v /home/Jone
{% endraw  %}
{% endhighlight %}

4. 现在你的登陆 shell 就是以 staff_u 用户运行

{% highlight bash %}
{% raw  %}
$ id -Z
staff_u:staff_r:staff_t:s0-s0:c0.c1023
{% endraw  %}
{% endhighlight %}

5. 如果你需要执行系统管理操作，可使用 sudo 进行提权，这和原来一模一样

{% highlight bash %}
{% raw  %}
$ sudo id -Z
staff_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
{% endraw  %}
{% endhighlight %}

## 广告

最后，插播广告。Fedora 社区源正在使用 SELinux 加固软件，目前已完成了 sogoupinyin。

安装 sogoupinyin SELinux 模块，禁止 sogou 访问网络：

{% highlight bash %}
{% raw  %}
$ sudo dnf install sogoupinyin sogoupinyin-selinux
$ sudo setsebool -P sogou_access_network=0
{% endraw  %}
{% endhighlight %}

## 参考

- [TCSEC, Trusted Computer System Evaluation Criteria](http://csrc.nist.gov/publications/history/dod85.pdf)
- [SELinux Project](http://selinuxproject.org)
- [原文: Fedora 安装后需要做的第一件事](http://cm.fdzh.org/2015/10/31/2015-11-1-first-thing-after-installation-of-Fedora/)

感谢 [1dot75cm](http://cm.fdzh.org), 转载请注明出处。

-- EOF --
