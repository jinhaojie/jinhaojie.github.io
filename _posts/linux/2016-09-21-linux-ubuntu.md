---
layout: post
title: ubuntu(持续更新)
description: linux & ubuntu
keywords: ubuntu
category : os
tags : [ubumtu , ubuntu系统]
---

#### 用sysv-rc-conf 代替redhat的chkconfig
>安装：`sudo apt-get isntall sysv-rc-confchank`

#### 查看默认启动级别
>通过`runlevel`命令查看启动级别

#### linux启动级别,可以通过man runlevel来查看
>
|Runlevel|Target|
|--------|------|
|0|poweroff.target|
|1|rescue.target|
|2, 3, 4|multi-user.target|
|5| graphical.target|
|6|reboot.target|


#### 定时任务（cron服务)
1. 服务的开启与停止
```
service cron start
service cron stop
service cron restart
service cron status
```
2. 打开cron的日志记录
sudo vi /etc/rsyslog.d/50-default.conf
去掉下面行的注释
```
cron.*              /var/log/cron.log
```
3. 编辑crontab

   crontab -e 
   
   分 时 天 月 星期 command
4. 


