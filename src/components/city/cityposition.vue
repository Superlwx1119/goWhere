<template>
	<div class="position" ref='wapper'>
		<div>
			<h2>当前城市</h2>
			<div class="current">
				<p>{{this.$store.state.city}}</p>
			</div>
			<h2>热门城市</h2>
			<div class="hotcity" >
				<p v-for="(item,key) of hotCity" @click="handleClickCity(item.name)" :key='item.id'>{{item.name}}</p>
			</div>
			<div class="cityList">
				<div v-for="(city,key) of cities" :ref='key' :key='key'>
					<h2>{{key}}</h2>
					<p v-for="(item,key) of city"  @click="handleClickCity(item.name)" :ref="key" :key='item.id'>{{item.name}}</p>
				</div>
			</div>
		</div>
	</div>
	
</template>

<script>
	import BScroll from 'better-scroll'
	export default{
		name:'position',
		props:{
			city:String,
			hotCity:Array,
			cities:Object,
			better: String
		},
		methods: {
		    handleClickCity (city) {
		      this.$store.dispatch('changeCity', city)
		      this.$router.push('/')
		    }
		  },
		watch:{
			better () {
			      if (this.better) {
			      	console.log(this.$refs[this.better][0])
			        this.scroll.scrollToElement(this.$refs[this.better][0])
			      }
			    }
		},
		mounted(){
			this.scroll= new BScroll (this.$refs.wapper)
		}
	}
</script>

<style scoped>
	.cityList h2{
		
		background: #eeeeee;
		color: #666666;
		border-bottom: 1px solid #dedede;
		border-top: 1px solid #dedede;
		height: .5rem;
		line-height: .5rem;
		text-indent: .2rem;
	}
	.cityList p{
		height: .5rem;
		border-bottom: 1px solid #dedede;
		text-indent: .2rem;
		line-height: .5rem;
	}
	.position{
		overflow:hidden;
	    position: absolute;
	    top: 1.2rem;
	    left:0;
	    right:0;
	    bottom:0;
	}
	.position h2{
		background: #eeeeee;
		color: #666666;
		border-bottom: 1px solid #dedede;
		border-top: 1px solid #dedede;
		height: .5rem;
		line-height: .5rem;
		text-indent: .2rem;
	}
	.hotcity{
		margin-bottom: .2rem;
	}
	.hotcity{
		display: flex;
		flex-wrap: wrap;
	}
	.current p{
		margin-bottom: .2rem;
		width: 25%;
		margin:.2rem 0 .2rem .35rem;
		height: .5rem;
		border: 1px solid #dedede;
		border-radius: 5px;
		line-height: .5rem;
		text-align: center;
	}
	.hotcity p{
		width: 25%;
		margin:.2rem 0 0rem .35rem;
		height: .5rem;
		border: 1px solid #dedede;
		border-radius: 5px;
		line-height: .5rem;
		text-align: center;
	}
</style>