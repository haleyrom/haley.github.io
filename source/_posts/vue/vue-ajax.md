---
layout: pose
title: axios的post请求后台（ThinkPHP5）接收不到数据
date: 2017-12-05 11:10:04
tags: [vue,js]
categories: [前端,vue]
cover: https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=1243750124,1921701882&fm=26&gp=0.jpg
---
最近做vue项目，做分页的功能，使用post给后台发送数据，使用接口还是工具（postman）都可获取数据，唯独axios获取不到；经过排除，发现这与axios的post传参格式有关系；

```
 this.$axios({
    method: 'post',
    url:url,
    params: {
        seller_id:seller_id
    }
}).then((res)=>{
 
})
```
在使用axios时，要注意到配置选项中包含params和data两者，以为他们是相同的，实则不然。 
因为params是添加到url的请求字符串中的，用于get请求。而data（form-data）是添加到请求体（body）中的， 用于post请求。

## 解决方法
### 方法1:

配置如下：
在main.js里 设置配置，修改Content-Type

```
import axios from 'axios';
axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded';
Vue.prototype.$axios = axios;
```

> Content-Type须配置为application/x-www-form-urlencoded，以数据量格式进行数据传输（不兼容ie）

### 方法2：（推荐）
安装qs,在 main.js里引入并且对数据进行序列化

```
import axios from 'axios';
import qs from 'qs';
Vue.prototype.$qs = qs;
```
或者

```
import qs from 'qs';
axios.interceptors.request.use((config) => {
    config.data = qs.stringify(config.data);
    return config;
}, function(error) {
    return Promise.reject(error);
});
```



