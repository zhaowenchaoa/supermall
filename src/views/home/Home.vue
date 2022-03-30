<template>
 <div id="home">
    <nav-bar class="home-nav">
      <div slot="center">购物街</div>
    </nav-bar>
    <home-swiper :banners="banners"></home-swiper>
    <recommend-view :recommends="recommends"></recommend-view>
 </div>
</template>

<script>
import NavBar from 'components/common/navbar/NavBar'
import HomeSwiper from './childComps/HomeSwiper'
import RecommendView from './childComps/RecommendView'

// 这里之所以用大括号  是因为得home.js没有导出
import {getHomeMultidata} from 'network/home'



export default {
 name:"Home",
 components: {
   NavBar,
HomeSwiper,
RecommendView
 
 },
 data(){
   return {
     banners:[],
     recommends :[]
   }
 },
 created () {
   // 1. 请求多个数据
   // 箭头函数得this指向最近作用域得
   // 因为这里面是函数 所以是局部变量 这里面的数据我们全局变量用不了  所以我们在data里面设置一个变量 然后把这个数据传给全局变量 这里利用了箭头函数得this
   getHomeMultidata().then(res =>{
     
     
     this.banners = res.data.banner.list;
     this.recommends =  res.data.recommend.list;
   })
 }
}
</script>

<style scoped>
.home-nav{
  background-color: var(--color-tint);
  color: #fff;
}
</style>