---
title: Laravel new 项目缺少Vendor（composer忽略php7版本）
date: 2017-06-04 15:23:11
tags: [php,laravel]
categories: [后端,php]
cover: https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=1091292349,1608405974&fm=26&gp=0.jpg

---

## 错误
> Your requirements could not be resolved to an installable set of packages.

![这里写图片描述](https://img-blog.csdn.net/20180428160446447?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzE1NDEzMDA5/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

## 原因
> php不匹配composer.json要求的版本

## 解决方法
>composer install --ignore-platform-reqs  
composer update --ignore-platform-reqs
composer create-project --prefer-dist laravel/laravel blog "5.5.*"

## 其他情况
未满足一下条件
 > 
 - PHP >= 7.0.0
 - PHP OpenSSL 扩展 
 - PHP PDO 扩展 
 - PHP Mbstring 扩展 
 - PHP Tokenizer扩展 
 - PHP XML 扩展
 