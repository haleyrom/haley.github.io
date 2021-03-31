---
title: php7+apache2.4+mysql 环境配置(window环境)
date: 2016-12-03 16:20:37
tags: [php,apache,mysql,window]
categories: [后端,php]
cover: https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=182737026,1808659085&fm=26&gp=0.jpg
---
简要：最近，小主从事PHP开发。特将最近如何搭建php7的过程记录在此！希望有需要，可以借鉴！( 电脑必须win7 sp1以上， .netframework4 ) Windows7安装php7，Win7+php7+apache2.4，成功启动。

### 下载php7、apache2.4、mysql

    首先下载php7的windows压缩包，到这里下载http://windows.php.net/download/。对应版本：Php7  VC14 x86 Thread Safe  

　　我选择的是php7的这个版本，由于它是vc14编译的，这意味着需要安装vc2015(即vc14)运行时环境，同时需要Apache2.4才可以运行php7 。

*  vc2015到这里下载：http://www.microsoft.com/zh-cn/download/details.aspx?id=48145  运行安装。

   需要注意，安装vc14必须开启这3个服务，否则一定会安装失败：

*  apache2.4到这里下载：Apache 2.4.17 Win32  http://www.apachelounge.com/download/ 对应版本号：httpd-2.4.17-win32-VC14.zip    

*  mysql  https://pan.baidu.com/s/1bo5Or63（推荐安装此版本，其他版本mysql会出现无法关闭的情况，视图界面即装即用；）

*  将php7的windows压缩包、Apache2.4解压，如我的路径是：

> D:\Server\Apache24
  D:\Server\Php
　D:\Server\Mysql
  D:\Server\WWW   (存放php网站脚本的目录，DocumentRoot.)

### 配置httpd.conf和php.ini ：
#### 打开apache24/conf/httpd.conf

```angular2
 修改：ServerRoot "D:/Server/Apache24"
 修改：DocumentRoot "D:/Server/WWW/ "
 添加 ：（注意phpIniDir项在上面） php7对apache的处理接口
 
 PHPIniDir "D:/Server/Php"
 AddType application/x-httpd-php .php .html .htm
 LoadModule php7_module "D:/Server/Php/php7apache2_4.dll"
```
#### 配置php.ini。 打开php目录，复制1个php.ini-development ，修改为php.ini。

   打开php.ini， 找到 ;extension_dir = "D:/Server/Php/ext"  ，把前面的分号去掉。

　（必须指定扩展路径，否则php7启动不了。一般开启ext扩展目录之后，就可以成功在命令行启动php7，如果仍然不成功，说明你的php路径没有添加到 环境变量中（或者你的环境变量有旧的php版本使用））

 ### 把apache24加入windows服务，并启动apache：
```angular2
 Cmd命令行，进入d盘，然后打开目录，运行httpd  –k install
 D:
 Cd   D:\Server\Apache24\bin
 httpd  –k install
　httpd  –k start
```
　　　　
这样，apache和php7就启动了。

在 D:/web/www/ 创建1个phpinfo.php文件

访问：http://127.0.0.1/phpinfo.php  实际运行结果。如果你有问题，咨询QQ群 866437035 给你答案。  


（另外提供了1个php7集成环境打包： http://pan.baidu.com/s/1qXwjpF2  ，注意：一旦自己搭建后，就尽量不要安装集成环境；会早成一定的冲突！）
