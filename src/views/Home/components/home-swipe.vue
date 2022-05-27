<template>
<van-swipe class="my-swipe" :autoplay="3000" indicator-color="white">
  <van-swipe-item v-for="item in list" :key="item.imgSrc" >
  <img :src="item.imgSrc"/>
  </van-swipe-item>
</van-swipe>
</template>

<script setup lang="ts">
import { ref } from "vue"
import axios from "axios"

const list=ref<ISwiper[]>([])

// ts的接口用于标记数据格式,使用接口时有类型提醒
interface ISwiper{
  imgSrc: string
  link: string
}

axios({
  url: "/swiperList",
  method: "get",
}).then(res=>{
  list.value=res.data.result
})
</script>

<style lang="less" scoped>
.my-swipe{
  img{
    width: 100%;
  }
}
</style>
