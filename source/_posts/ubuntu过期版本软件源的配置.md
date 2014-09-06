title: ubuntu过期版本软件源的配置
date: 2014-09-06 16:14:41
tags:
---

* 众所周之,ubuntu中软件的安装都是依赖于源,体现在命令中即`apt-get`.
* ubuntu的版本分维护四年的lts版本及半年一更新的普通版本,ubuntu对于版本依赖的软件源的维护时间与版本时间相同.
* 比如当14.04(Trusty Tahr)版本发行后, 13.10(Saucy Salamander)版本及软件源官方即不再维护
* 如果你还在使用13.10版本时,在使用apt-get update时会报404 nout found.

###### 此时有两种方式来解决此问题

1. cd /etc/apt; sudo vim source.list; 将其中的saucy替换为trusty.此种改变有可能会引起一些未知问题,因为软件源是与发行版本相对应的.
2. cd /etc/apt; sudo vim source.list; 将其中的cn.archive.和security.替换为old-releases.; 可完美解决软件源的问题
