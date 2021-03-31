---
layout: pose
title: Laravel 自带时间处理函数 
date: 2017-07-04 15:29:42
tags: [php,laravel]
categories: [后端,php]
cover: https://ss1.bdstatic.com/70cFuXSh_Q1YnxGkpoWK1HF6hhy/it/u=2516212805,4167059458&fm=26&gp=0.jpg
---
>Carbon 是继承自 PHP DateTime 类 的子类，但比后者提供了更加丰富、更加语义化的 API。其中一个比较实用的 API 就是 diffForHumans 方法，几乎每个用 Laravel 构建的项目中都有用到它。

比如，一个博客系统里的文章发布时间，显示格式可能就像下面这样：
```
**距离现在时间**     **显示格式**
	< 1小时           xx分钟前
	1小时 - 24小时     xx小时前 
	1天 - 15天         xx天前
	> 15天            直接显示日期
```

** 第一步：
本地化 Carbon。在 AppServiceProvider 的 boot 方法中添加 Carbon::setLocale('zh')。
![这里写图片描述](https://img-blog.csdn.net/20180503082345106?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzE1NDEzMDA5/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

```
Carbon::setLocale('zh');
```

** 第二步：
在 Model 中设定要人性化显示的字段。以 Article Model 的 created_at 字段为例。
![这里写图片描述](https://img-blog.csdn.net/20180503082441347?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzE1NDEzMDA5/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

```
 public function getCreatedAtAttribute($value){
	   return Carbon::createFromFormat('Y-m-d H:i:s', $value)->diffForHumans();
 }
```
下面就可以直接使用了。

```
$article->created_at;
```

