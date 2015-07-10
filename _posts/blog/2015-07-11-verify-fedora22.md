---
layout: post
author: tvvocold
category: blog
title:  Windows 下校验 Fedora ISO 文件
tags: Windows Fedora22       
image: http://7o51u6.com1.z0.glb.clouddn.com/1295684929_ddvip_2818.png
---

在准备安装 Fedora 22 前，对下载的 ISO 安装文件进行校验是很有必要的。下面我们进行对 Fedora 22（64bit) ISO 文件的校验。

1, 点击开始 > 运行 > cmd，输入 PowerShell 进入 Windows PowerShell

2，进入Fedora ISO文件所在的目录，如

> $ cd $HOME\Downloads\

3，按顺序运行以下命令:

> $image = "Fedora-Live-Workstation-x86_64-22-3.iso"
> $checksum_file = "Fedora-Workstation-22-x86_64-CHECKSUM"
> $sha256 = New-Object -TypeName System.Security.Cryptography.sha256CryptoServiceProvider
> $expected_checksum = ((Get-Content $checksum_file | Select-String -Pattern $image) -split " ")[0].ToLower()

4, 开始进行校验：

> $download_checksum = [System.BitConverter]::ToString($sha256.ComputeHash([System.IO.File]::ReadAllBytes("$PWD\$image"))).ToLower() -replace '-', ''

5, 查看结果是否和 [官网提供的预期结果](https://getfedora.org/static/checksums/Fedora-Workstation-22-x86_64-CHECKSUM) 一致：

> $echo "Download Checksum: $download_checksum" 
