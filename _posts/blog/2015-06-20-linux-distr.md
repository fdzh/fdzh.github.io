---
layout: post
author: tvvocold
category: blog
title:  Linux 发行版是什么，它又与Linux内核有什么联系？  
tags: lfs101x Linux家族          
image: http://7o51u6.com1.z0.glb.clouddn.com/49d503bf47879ffe8a169dd81c744d83_b.jpg
---

Linux 发行版是什么，它又与Linux内核有什么联系？
-
Linux内核是计算机操作系统的核心。一个完整的 Linux发行版包括了内核与一些其他与文件相关的操作，用户管理系统，和软件包管理器等一系列软件。每个工具都是整个系统的一小部分。这些工具通常都是一个个独立的项目，有相应的开发者来开发及维护。

前面提到的Linux内核，包括现行版本，以及历史版本（即更早发布的版本）都可以在 www.kernel.org 找到。Linux的众多发行版可能是基于不同的内核版本的。例如：流行的 RHEL6发行版是基于很老但是很稳定的 2.6.32 版本的Linux内核的。其他的一些发行版可能会很快的更新以适应最新的内核版本。需要特别注意的一点是，内核并不是一个非此即彼的命题，例如RHEL6就在2.6.32的内核中引进了新版本内核的许多改进。

各发行版提供的其他基本工具和组成部分还有包括以下的内容：C/C++编译器，gdbdebugger 调试工具，核心系统库应用程序，用于在屏幕上绘图的底层接口以及高级的桌面环境，以及供安装和更新包括内核在内的众多组建的系统

众多不同的Linux发行版满足了不同用户及组织的不同需求。大型商业机构通常倾向于使用来由 Red Hat、 SUSE 及 Canonical (Ubuntu)提供的发行版。

Fedora 是基于RHEL，CentOS，Scientific Linux, 和Oracle Linux的社区版本。相比RHEL，Fedora打包了显著的更多的软件包。其中一个原因是，多样化的社区参与Fedora的建设;它不只是一家公司。在这个过程中，CentOS用于活动，演示和实验，因为它是对最终用户免费提供的，并具有比Fedora的一个更长的发布周期（通常每隔半年左右发布一个新版本）。

SUSE, SUSE Linux Enterprise Server (SLES), 和openSUSE 之间的关系类似于 Fedora, Red Hat Enterprise Linux, 和CentOS的关系。

Debian是包括Ubuntu在内许多发行版的上游，而Ubuntu又是Linux Mint及其他发行版的上游。Debian在服务器和桌面电脑领域都有着广泛的应用。Debian是一个纯开源计划并着重在一个关键点上，稳定性。它同时也提供了最大的和完整的软件仓库给用户。

信息来自: [Linux 基金会制作的 Linux 入门教程翻译项目](https://github.com/fdzh/LFS101x)
