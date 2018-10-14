<template>
	<div class="nav_list">
		 <swiper :options="swiperOption">
		 	<swiper-slide v-for='(swiperList,index) of pages' :key='index'>
		        <div class="icon-warpper" v-for="item of swiperList" :key='item.id'>
		          <img :src="item.imgUrl" class="icon-img" />
		          <p class="icon-desc">{{item.desc}}</p>
		        </div>
		    </swiper-slide>
		     <div class="swiper-pagination"  slot="pagination"></div>
		 </swiper>
	</div>
</template>

<script>
	export default{
		name:'nav_list',
		props:{
			iconList:Array
		},
		computed:{
			pages(){
				const pages = []
		        this.iconList.forEach((item, index) => {
		        const page = Math.floor(index / 8)
		        if (!pages[page]) {
		          pages[page] = []
		        }
		        pages[page].push(item)
		      })
		      return pages
			}
		},
		data(){
			return {
			      swiperOption: {
			      	 pagination: '.swiper-pagination',
			      }
			}
		}
	}
</script>

<style scoped>
	.swiper-slide{
		display: flex;
		flex-wrap: wrap;
		height: 3.3rem;
		align-content: center;
	}
	.icon-warpper{
		width: 25%;
		text-align: center;
		margin-bottom: .15rem;
	}
	.icon-img{
		width: 1rem;
		height: 1rem;
	}
</style>