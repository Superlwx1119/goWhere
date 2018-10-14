<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
    window.onresize = window.onload = function(){
       let deviceWidth = document.documentElement.clientWidth;
       if(deviceWidth > 640) deviceWidth = 640;
       document.documentElement.style.fontSize = deviceWidth / 6.4 + 'px';
    };
import Header from './components/header/Header'
import Home from './components/Home'
import City from './components/city/city'
import 'swiper/dist/css/swiper.css'

import { swiper, swiperSlide } from 'vue-awesome-swiper'
export default {
  name: 'App',
  components:{
  	Header,
  	Home,
  	swiper,
    swiperSlide
  }
}
</script>

<style>
</style>
