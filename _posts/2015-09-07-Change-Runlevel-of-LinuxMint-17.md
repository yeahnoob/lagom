---
layout: post
title: Change Runlevel of Linux Mint 17
comments: true
categories:
- blog
---

改变 Linux Mint 17.1的默认启动级别（启动后进入多用户命令行界面）

---

## 问题描述

之前的一些Linux 发行版本，直接输入`init 3`就可以进入跳出X窗口图形界面，进入命令行模式。
但是在服务器上虚拟的Linux Mint 17.1版本，输入`init 3`即不转入命令行界面，也不报错。

## 问题分析
对比实际系统中的运行的模块，同时参考网上找到的一些很笼统的信息，结合起来可以总结如下：

  -- Debian 系列的很多 Linux 发行版本，并没有使用默认的 Linux 启动级别(Runlevel)设置。
  -- 通过一些方式改变 Runlevel 后，系统也不会自动退出图形界面。
  -- Linux Mint 17.1 使用单独的 mdm (MDM Display Manager) 模块，管理图形界面的启动。
  -- 当前 Ubuntu 比如 14.04 版本的中，也使用单独的 lightdm (Lightweight Display Manager) 模块来管理图形界面启动。

## 解决方法


`/etc/init/rc-sysinit.conf` 中修改对应字段为
{% highlight Bash %}
env DEFAULT_RUNLEVEL=3
{% endhighlight %}

`/etc/init/mdm.conf` 中修改对应字段为
{% highlight Bash %}
#start on ((filesystem
#           and runlevel [!06]
#           and started dbus
#           and plymouth-ready)
#          or runlevel PREVLEVEL=S)
#
#stop on runlevel [016]

start on ((filesystem
           and runlevel [!036]
           and started dbus
           and plymouth-ready)
          or runlevel PREVLEVEL=S)

stop on runlevel [0136]
{% endhighlight %}

这样修改以后重启就能正常进入多用户命令行模式。

