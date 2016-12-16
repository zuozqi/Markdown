---
title: Linux Notes 
date: 2016年10月3日21:29:07
categories: 工具
tags: [Linux,Note]
---

常见命令
===

日期时间
---
<!--more-->


`date` 查看系统时间  `+%Y--%M:D` 
 `hwclock`  查看主板上的硬件时间
 `cal`  查看日历

输出查看
---

 `echo` 原封不动返回
 `cat`  查看文件内容，所有
 `head`  ( `tail` )查看文件头 `后` 几行默认十行  -n 10  (-f 追踪文件更新，不退出，一直看，查看日志)
 `more` , ` `less` ,带翻页显示，可以上(上下)翻页。
 
查看硬件信息
---
 `lspci` , `lsusb`(-v 详细) , `lsmod` (驱动)

关机重启
---
 `shutdown`  -h 关机 -r重启 时间(+X X分钟后)
 `poweroff`  立刻关机
 `reboot`  立刻重启

归档压缩
---
 `zip 压缩后的名字.zip 被压缩的文件`
 `unzip 压缩文件.zip` 
 `gzip` 
 `tar`  归档命令，打包用的
-cvf 名字.tar 被归档的文件 创建一个归档，不会压缩
-xvf x.tar 在当前目录解开归档
-cvzf 归档后gzip压缩  .tar.gz

查找
---
 `locate keyword` 快查找，查数据库，需要更新
 `update db`  更新数据库
 `find`  
 `find . -name *linuxcast*` 
 `find / -perm 777`  权限777
 `find / -type d`  目录文件
 `find . -name "a*" -exec ls -l {} \;`  查找a开头的文件， 执行ls -l ，外面是固定格式


vi编辑器
===

命令行界面  ->vim

`vim 目标路径文件`  如果存在则打开，不存在就创建

使用详见vi教程

获取帮助
===
help
---

 `-h` , `--help` ，查看使用方法，参数

man
---

将查看的命令作为参数，打印出来像手册

info
---

与man使用类似，但信息更为详细


网络基础
===

 `lspci` 
 `ifconfig` 查看接口信息
 `ifup eth0`  启用eth0接口
 `setup`  文本界面，配置网络，一步一步来
 `ping` 
 `traceroute` 
 `mtr` 实时更新，检测网络质量
 `hostname`  临时修改主机名
永久修改 etc/sysconfig/network



