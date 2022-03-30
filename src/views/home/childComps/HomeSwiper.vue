<template>
  <swiper>
      <swiper-item v-for="item in banners" :key="item.acm">
        <a :href="item.link">
          <img :src="item.image" alt="">
        </a>
      </swiper-item>
    </swiper>
</template>

<script>
// import Swiper from 'components/common/swiper/Swiper'
// import SwiperItem from 'components/common/swiper/SwiperItem'
// 这个是把swiper里面创建得index.js文件导出 因为那里面导出对象 这里面直接导出里面写的两个 比上面方便
import {Swiper,SwiperItem} from 'components/common/swiper/index'

export default {
    name:"HomeSwiper",
    props: {
        banners:{
            type:Array,
            default(){
                return []
            }
        }
    },
    components: {
        Swiper,
        SwiperItem
    }
}
</script>

<style>

</style>