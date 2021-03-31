---
layout: pose
title: 'Linux下安装Beego：go install: cannot install cross-compiled binaries when GOBIN is set'
date: 2018-01-15 11:14:41
tags: [go,bee,beego,gobin]
categories: [后端,go]
cover: https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=373846818,1266499745&fm=26&gp=0.jpg
---


# Linux下安装Beego出错

## 问题：go install: cannot install cross-compiled binaries when GOBIN is set

遇到这个问题一般是在环境变量中设置了 GOBIN 可以打开 /etc/profile 把这个变量注释掉就，执行 source /etc/profile生效即可同样安装完成之后需要在环境变量中追加bee的路径

### 解决思路
1. 注释GOBIN选项，并在 /etc/profile 文件中设置GOPATH/bin（永久）

```
export PATH=$GOPATH/bin:$PATH 
```
重新生成配置

```
source /etc/profile
```
可能遇到的问题：添加之后执行bee不成功。
查看bee的所在路径 ：

```
 echo $GOPATH //获取GOPATH的路径 本人是在/data/www/go:
 find /home/chun/go -name "bee" //查找目录的含bee的文件夹
```
输出：

```
/data/www/go/bin/linux_386/bee
/data/www/go/src/github.com/beego/bee
/data/www/go/pkg/linux_386/github.com/beego/bee
```
这里可以看到我的linux系统上bee的安装路径和正常不一样，在linux_386下面，接下来只需把/home/chun/go/bin/linux_386添加到环境变量就ok了。

```
export PATH=$GOPATH/bin/linux_386:$PATH
source /etc/profile
```

2. 在GOPATH下删除GOBIN设置（暂时）

```
cd $GOPATH
unset GOBIN
```

>交流沟通：QQ群866437035
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190220114346945.jpg) 
