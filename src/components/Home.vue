<template>
	<div class="home">
		<Header :city='city'/>
		<Swiper :swiperList='swiperList'/>
		<SwiperNav :iconList='iconList'/>
		<Hot :recommendList='recommendList'/>
		<Weekend :weekendList='weekendList'/>
	</div>
</template>

<script>
	import Header from './header/Header'
	import Swiper from './Swiper'
	import SwiperNav from './swiperNav'
	import Hot from './Hot'
	import Weekend from './weekend'
	import axios from 'axios'
	export default{
		name:'Home',
		components:{
			Header,
			Swiper,
			SwiperNav,
			Hot,
			Weekend
		},
		 data () {
		    return {
		      city: '',
		      swiperList: [],
		      iconList: [],
		      recommendList: [],
		      weekendList: []
		    }
		  },
		methods: {
		    getHomeInof () {
		      axios.get('/static/mock/index.json')
		        .then(this.getHomeInfoSucc)
		    },
		    getHomeInfoSucc (res) {
		      res = res.data
		      if (res.ret && res.data) {
		        const data = res.data
		        this.city = data.city
		        this.swiperList = data.swiperList
		        this.iconList = data.iconList
		        this.recommendList = data.recommendList
		        this.weekendList = data.weekendList
		      }
		    }
		  },
		  mounted () {
		    this.getHomeInof()
		  }
	}
</script>

<style>
</style>