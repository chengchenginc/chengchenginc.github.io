---
layout:     post
title:      "window使用docker toolbox搭建开发环境"
date:       2016-09-25 12:00:00
header-img: "assets/images/post-bg-01.png"
tags: [docker]
categories: [developer]
---

<p>
	本文主要介绍下window环境下 docker Toolbox的使用以及开发所需依赖环境安装，我们以安装mysql、redis两个为例，简单介绍下在window下的使用，提高我们开发环境搭建效率。
</p>

<h3>安装mysql</h3>
<h4>第一步:</h4>
<p>
	启动Kitematic，以及docker Terminal
	<a href="javascript:;">
    <img src="{{ site.baseurl }}/assets/images/post-sample-01.png">
	</a>
</p>

<h4>第二步:</h4>
pull mysql镜像
```docker pull mysql```

<h4>第三步:</h4>
容器化运行mysql进行,并打开交互命令窗口(端口可以-p指定,也可以通过Kitematic设置)
	```
		docker run --name mysql -it mysql /bin/bash
	```

<a href="javascript:;">
	<img src="{{ site.baseurl }}/assets/images/post-sample-02.png">
</a>
