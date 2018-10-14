<template>
	<div class="city">
		<CityHeader/>
		<Sreach :cities='cities'/>
		<Position :city='city' :better='better' :cities='cities' :hotCity='hotCity'/>
		<Fixed :cities='cities' :better='better' @change="handleClickBetter"/>
	</div>
</template>

<script>
	import CityHeader from './cityHeader'
	import Sreach from './sreach'
	import Position from './cityposition'
	import CityList from './cityList' 
	import Fixed from './fixed' 
	import axios from 'axios'
	export default{
		name:'city',
		components:{
			CityHeader,
			Sreach,
			Position,
			CityList,
			Fixed
		},
		data(){
			return{
				city:'',
				hotCity:[],
				cities:{},
				better: ''
			}
		},
		methods:{
			handleClickBetter (better) {
		      this.better = better
		    },
			getCityInfo () {
		      axios.get('/static/mock/city.json')
		        .then(this.getCityInfoSucc)
		    },
		    getCityInfoSucc(res){
		    	res=res.data;
		    	if (res.ret && res.data) {
			        const data = res.data
			        this.city = data.city
			        this.hotCity = data.hotCities
			        this.cities = data.cities
			      }
		    }
		},
		mounted () {
		    this.getCityInfo()
		  }
	}
</script>

<style>
</style>