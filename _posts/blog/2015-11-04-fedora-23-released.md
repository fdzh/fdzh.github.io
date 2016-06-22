---
layout: post
author: Bootingman
category: blog
title:  迟到的万圣节大餐 － Fedora 23 正式发布！ 
tags: fedora-23           
image: http://7o51u6.com1.z0.glb.clouddn.com/fedora-23-release-755x350.jpg
---

美国东部时间 2015 年 11 月 3 日 10 时，北京时间 11 月 3 日 23 时， Fedora Project 宣布 Fedora 23 正式发布，同时开放下载并可以由旧版本升级。这有可能是史上最好用的 Fedora ，三个主要的 Fedora 子版本都同时带来了最新的特性。

对于 Fedora Project 的 Matthew Miller 来说，这次 Fedora 23 的发布周期中有不少意外的惊喜：“我们差一点就赶上本来预定的万圣节日期了，那样的话就能给大家再一个惊喜了”。至于为什么会有延期， Miller 解释道， Fedora 的开发是一个混合的模式，一个是严格基于日期的模式，一个是根据功能是否就绪来定的模式，自从 Fedora 从上游集成了越来越多不是自己能控制的开源项目及以来，让时间变得精确就越来越困难了，虽然 Fedora 也很希望能准时发布。

> “我们在开发过程中不断修正我们最终的发布时间，同时在每一个重要时间节点前进行再确认”，Miller 说“通常来说，我们都能预估到可能会有延误，也会把它加入到我们的考量中”。

如果你早早就关注了 Fedora 23，想直接安装，不要犹豫马上来这里下载吧，官方下载地址：[https://getfedora.org](https://getfedora.org)，中国用户也可以使用 [Linux Story 的镜像下载](http://mirrors.linuxstory.org)，如果你已经在使用旧版本的 Fedora，请阅读 [使用 dnf 升级到 Fedora 23 的方法](http://hack.fdzh.org/item?id=1097) 。

#### Fedora 23 新特性：

- 利用编译器标志提高安全性，通过 [hardening](https://fedoraproject.org/wiki/Changes/Harden_All_Packages) 避免进程发生内存泄露，缓冲区溢出等问题
- 禁用存在漏洞的 SSL3, RC4 协议
- 支持最新的 [Mono 4](https://fedoraproject.org/wiki/Changes/Mono_4)
- 使用 [Python 3](https://fedoraproject.org/wiki/Changes/Python_3_as_Default) 作为默认版本
- 使用 CIL 编译器编译 SELinux 策略模块，使模块占用资源更少，载入更快
- 支持 Unicode 8.0，并添加新的 emojis
- [GNOME 3.18](https://help.gnome.org/misc/release-notes/3.18/)：更新文件管理器，新的 Calendar 和 Todo 应用
- [LibreOffice 5](https://www.libreoffice.org/discover/new-features/)：HiDPI 支持，UI 更新
- Builder IDE：基于 LLVM 的代码检查，自动补全
- [Firmware 更新](http://www.fwupd.org/)：允许更新固件
- [Wayland](http://wayland.freedesktop.org/)：计划在 Fedora 24 使用 Wayland 作为默认 X Server
- 添加 Cinnamon 桌面环境
- 更多请参阅 [Fedora 23 Release Note](https://docs.fedoraproject.org/en-US/Fedora/23/html/Release_Notes/index.html)
  

 ![](http://dn-copr.qbox.me/workstation-logo.png)
 
如果你是一名软件开发者，笔记本电脑用户，家庭用户，业余爱好者，或学生，[Fedora Workstation](https://getfedora.org/workstation) 应该是最适合你的版本。Fedora Workstation 包括最新的 [GNOME](https://www.gnome.org/gnome-3/) 桌面环境，可以满足每天的日常使用，简单方便，轻松舒适。体验漂亮好用的界面和功能强大的工具。

 ![](http://dn-copr.qbox.me/server-logo.png)
 
通过 [RoleKit](https://github.com/libre-server/rolekit) 工具，Fedora Server 可以使我们的服务管理更加简单，一个程序化的界面可以方便地进行快速部署，同时还有 [Cockpit](http://cockpit-project.org/) 这个远程网络管理界面。在 Fedora Server 23 中，你可以通过 Cockpit Admin Console 轻松管理 [Kubernetes](http://kubernetes.io/) 集群，也可以轻松的使用 kickstart 部署 FreeIPA 域控。所有的这些你都可以通过下载最新 [Fedora Server 23](https://getfedora.org/server) 镜像马上拥有。
 
 ![](http://dn-copr.qbox.me/cloud-logo.png)
 
通过 Fedora Cloud 构建可扩展的弹性云绝对是个好主意，Fedora Cloud Base 镜像提供了一个最小化的操作系统平台，可方便的用于 OpenStack，或者直接在 EC2 上部署。Fedora Atomic Host 提供了一个特别定制的系统来运行 Docker 容器和 Atomic Apps，解决问题更加直接和彻底。在 Fedora Cloud 23，Fedora Atomic Host 将会每两周保持更新一次，以保证用户获得最新的稳定技术。现在立即为你的私有云和 Vagrant box 下载 [Fedora Cloud](https://getfedora.org/cloud/) 镜像。

> 感谢来自 [Linux Story](http://www.linuxstory.org) 的 Bootingman 带来的报道！

