<template>
	<div class="swiper">
		 <swiper :options="swiperOption" v-if="swiperList.length" >
	    <!-- slides -->
	    <swiper-slide v-for="item of swiperList" :key="item.id">
	    	<a href="/city">
	    		<img class="swipe-img" :src="item.imgUrl">
	    	</a>
	    </swiper-slide>
	    <!-- Optional controls -->
	    <div class="swiper-pagination"  slot="pagination"></div>
  </swiper>
	</div>
</template>

<script>
import 'swiper/dist/css/swiper.css'
import { swiper, swiperSlide } from 'vue-awesome-swiper'
export default {
	  name:'Swiper',
	  props:{
	  	swiperList:Array
	  },
	  components: {
	    swiper,
	    swiperSlide
	  },
  		data(){
	  	return {
	        swiperOption: {
	        	loop:true,
	        	autoplay: 2000,
	        	pagination: '.swiper-pagination'
	        }
		}  
		}
  }
</script>

<style>
	.swiper{
		width: 100%;
		overflow: hidden;
		height: 2rem;
	}
	a{
		display: block;
	}
	img{
		height: 2rem;
		width: 100%;
	}
	/*.swiper-pagination-bullet{
		background: white;
		
	}*/
	.swiper-pagination{
		margin-top: .2rem;
	}
</style>