---
title: dokuwiki安装流程(不勾选MicroApache的方法)
date: 2021-04-12 11:32:32
tags: doku wiki install 安装 维基 杜库
---

## 前言
**最近看到公司的wiki系统就突然想自己搭一下试试，以下是效果展示**

![](/images/dokuwiki_show.png)
![](/images/dokuwiki_show2.png)
## dokuwiki下载
**dokuwiki下载地址: [https://download.dokuwiki.org](https://download.dokuwiki.org)**
**在这里我们不勾选MicroApache(Windows)，因为我们会自己安装php、webserver**
**中间语言部分根据需求勾选**
**右侧插件可按需求勾选**
**选完之后点击上面的Download按钮或者下方的Start Download 按钮，压缩包下载下来备用**
![](/images/dokuwiki_install.png)

## php下载
**php下载地址: [https://windows.php.net/download#php-8.0](https://windows.php.net/download#php-8.0)**
![](/images/php_install.png)
**下载后解压，无需安装**

## phpStudy下载
**phpStudy是一个PHP调试环境的程序集成包。该程序包集成最新的Apache+PHP+MySQL+phpMyAdmin+ZendOptimizer，一次性安装，无须配置即可使用**
**这里我下载的是phpStudy v8.1版本, 下载后安装**
**phpstudy下载地址: [https://www.xp.cn/download.html](https://www.xp.cn/download.html)**
![](/images/phpstudy_install.png)

**WebServer这里选择的是Apache，当然也可以选择其他的**
![](/images/phpstudy_show.png)

**双击这条信息，或者点击【管理】->【打开根目录】，将下载的dokuwiki压缩包解压后放到这里**
![](/images/phpstudy_show2.png)

**在浏览器输入localhost:80/dokuwiki/install.php，可进入dokuwiki安装网页，这里我默认用的是80端口，如果需要修改可在【管理】->【修改】->【端口】修改**
**在该网页的右上角可以选择语言，左上部分，设置wiki名称，以及超级用户的账号密码，还可以选择ACL政策，注意这里是对wiki的权限设置，下面是证书的选择，笔者目前对这些证书的区别还不是很了解，所以使用默认选择的**
**设置好后，点击【保存】**
![](/images/dokuwiki_install2.png)

**这样 DokuWiki就搭建完成了**
![](/images/dokuwiki_install3.png)
![](/images/dokuwiki_install4.png)

