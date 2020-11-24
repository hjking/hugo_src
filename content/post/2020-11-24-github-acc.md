---
comments: true
tags: ["github"]
categories: ["github"]
title: "加速 GitHub 的访问速度"
date: 2020-11-24T18:52:02+08:00
---

作为身在国内的孩纸，上网是件容易的事儿，但是要想自由的上网，那还真是个难事儿。以下列出几个上网必备技能，供大家交流学习。**(Keep Updating)**

## GitHub 镜像访问

- https://github.com.cnpmjs.org

- https://hub.fastgit.org

也就是说上面的镜像就是一个克隆版的 GitHub，你可以访问上面的镜像网站，网站的内容跟 GitHub 是完整同步的镜像，然后在这个网站里面进行下载克隆等操作。

## GitHub 下载文件加速

利用 Cloudflare Workers 对 github release 、archive 以及项目文件进行加速，部署无需服务器且自带CDN.

- https://gh.api.99988866.xyz

- https://g.ioiox.com

以上网站为演示站点，如无法打开可以查看开源项目：[gh-proxy-GitHub](https://hunsh.net/archives/23/) 文件加速自行部署。

## Github 加速下载

只需要复制当前 GitHub 地址粘贴到输入框中就可以代理加速下载！
地址：http://toolwa.com/github/


<!--more-->


## 加速你的 Github

- https://github.zhlh6.cn

输入 Github 仓库地址，使用生成的地址进行 git ssh 等操作

## 谷歌浏览器 GitHub 加速插件(推荐)

- [GitHub加速](https://chrome.google.com/webstore/detail/github%E5%8A%A0%E9%80%9F/mfnkflidjnladnkldfonnaicljppahpg/related)

## GitHub raw 加速

GitHub raw 域名并非 github.com 而是 raw.githubusercontent.com，上方的 GitHub 加速如果不能加速这个域名，那么可以使用 Static CDN 提供的反代服务。
将 raw.githubusercontent.com 替换为 raw.staticdn.net 即可加速。


## 通过 Gitee 中转 fork 仓库下载

访问 gitee 网站：https://gitee.com/ 并登录，在顶部选择“从 GitHub/GitLab 导入仓库” ，在导入页面中粘贴你的Github仓库地址，点击导入即可。等待导入操作完成，然后在导入的仓库中下载浏览对应的该 GitHub 仓库代码，你也可以点击仓库顶部的“刷新”按钮进行 Github 代码仓库的同步。

## 通过修改 HOSTS 文件进行加速

手动把cdn和ip地址绑定。

- 第一步：获取 github 的 global.ssl.fastly 地址
	
	访问：http://github.global.ssl.fastly.net.ipaddress.com/#ipinfo 获取cdn和ip域名。得到：199.232.69.194 https://github.global.ssl.fastly.net

- 第二步：获取github.com地址
	
	访问：https://github.com.ipaddress.com/#ipinfo 获取cdn和ip，得到：140.82.114.4 http://github.com。

- 第三步：修改 host 文件映射上面查找到的 IP

	windows系统：修改C:\Windows\System32\drivers\etc\hosts文件，在末尾处添加以下内容：

	> 199.232.69.194 github.global.ssl.fastly.net

	> 140.82.114.4 github.com
