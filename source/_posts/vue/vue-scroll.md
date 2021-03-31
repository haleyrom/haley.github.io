---
title: vue-seamless-scroll在vue3.0引入
date: 2018-03-22
tags: [vue,js]
categories: [前端,vue]
cover: https://ss0.bdstatic.com/70cFuHSh_Q1YnxGkpoWK1HF6hhy/it/u=3280178027,2728676409&fm=26&gp=0.jpg
---
背景：vue-seamless-scroll 是目前vue无限滚动插件中相对比较好用的一个。刚好项目需要做个列表无限滚动。

官方参考文档：https://chenxuan0000.github.io/vue-seamless-scroll/zh/guide/

> 在官方文档中，未涉及到对createApp的引用。为此展示代码给予参考

```vue
<vue-seamless-scroll :data="listData"  :class-option="classOption" class="seamless-warp">
  <ul id="ul1" class="item" >
     <li v-for="item in listData" v-bind:key="item.id"></li>
  </ul>
</vue-seamless-scroll>
 
import vueSeamlessScroll from 'vue-seamless-scroll/src'

setup(){
    const classOption = () =>{
          return {
            step:0.2,//数值越大滚动越快
            direction: 2,//滚动方向：0:向下，1：向上，2：向左，3：向右
            limitMoveNum: 100,//数据量：listData.length
            hoverStop:true,//是否开启鼠标悬停stop
            openWatch:true,//开启数据时监控刷新dom
            singleHeight: 0, // 单步运动停止的高度(默认值0是无缝不停止的滚动) direction => 0/1

            singleWidth:0,// 单步运动停止的宽度(默认值0是无缝不停止的滚动) direction => 2/3
            waitTime:1000// 单步运动停止的时间(默认值1000ms)

          }
    };
    return {
      classOption
    };
  }
）
```