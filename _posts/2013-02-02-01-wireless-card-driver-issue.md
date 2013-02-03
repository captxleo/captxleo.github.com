---
layout: post
title: 解决Ubuntu 12.10下无线网卡驱动问题
---
1.	update-manager --> settings --> additional drivers --> 选择相应的网卡驱动
2.	执行如下命令

		sudo apt-get install linux-headers-generic
		sudo apt-get install --reinstall bcmwl-kernel-source
		sudo modprobe wl
