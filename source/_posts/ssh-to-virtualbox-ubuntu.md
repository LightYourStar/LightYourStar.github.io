---
title: ssh to virtualbox ubuntu
date: 2022-04-20 18:18:04
tags: virtualbox ubuntu ssh root permission
---
### 描述：通过ssh root连接本地用virtualbox创建的ubuntu虚拟机失败
```bash
$ ssh root@10.7.132.xx
root@10.7.132.xx's password:
Permission denied, please try again.
```
### 方案：
在virtualbox的ubuntu中（10.7.132.xx的服务器）vim/etc/ssh/sshd_config
找到PermitRootLogin without-password 改为 PermitRootLogin yes

如下图
![](/images/ssh2virtualbox_ubuntu1.png)
重启SSH服务
```bash
$ sudo service ssh restart
```
