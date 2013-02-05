---
layout: post
title: Ubuntu下安装配置goagent
---
1.	[下载goagent客户端](https://code.google.com/p/goagent/)
2.	修改 local/proxy.ini 中的 [gae] 下的 appid (多appid用|隔开)
3.	上传服务端，在 server 目录下运行 `python uploader.zip`
4.	安装 gevent

<pre style="overflow: auto;">
sudo apt-get install python-dev
sudo apt-get install curl
curl -L -O https://github.com/python-greenlet/greenlet/archive/0.4.0.tar.gz && tar xvzpf 0.4.0.tar.gz && cd greenlet-0.4.0 && sudopython setup.py instal
curl -L -O https://github.com/downloads/SiteSupport/gevent/gevent-1.0rc2.tar.gz && tar xvzpf gevent-1.0rc2.tar.gz && cd gevent-10rc2 && sudo python setup.py install 
</pre>
	
5.	上传完服务端并设置好 proxy.ini 之后，在终端直接运行 `python proxy.py` 即可
	-	第一次运行时使用管理员权限，以便导入证书
	-	使用以下命令让 goagent 在后台运行

			python proxy.py > /tmp/goagent_tmp 2>&1 &

6.	在 firefox 上安装插件 foxyproxy
	-	配置代理地址和端口：127.0.0.1：8087
	-	导入安全证书
		
			edit --> preferences --> advanced --> encryption --> view certificates --> authorities --> import --> 选择 goagent_home_path/local/ca.crt
