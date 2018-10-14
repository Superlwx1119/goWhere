<template>
	<div class="detailHeader">
		<router-link to='/' v-show="showAbs">
			<div class="backBig">
				<p class="iconfont icon-custom-back"></p>
			</div>
		</router-link>
		<div class="header" v-show="!showAbs" :style="opacityStyle">
			<router-link class='back' to='/'>
			<span class="iconfont icon-custom-back"></span>
			</router-link>
			<p class="choseCity">景点详情</p>
		</div>
	</div>
</template>

<script>
	export default{
		name:'detailHeader',
		data(){
			return{
				showAbs: true,
			    opacityStyle: {
			      opacity: 0
			    }
			}
		},
		methods:{
			windowScroll(){
				const top=document.documentElement.scrollTop
				if(top>30){
					const opacity=top/100
					this.opacityStyle={opacity:opacity>1?1:opacity}
					this.showAbs=false
				}else{
					this.showAbs=true
				}
				
			}
		},
		mounted(){
			window.addEventListener('scroll',this.windowScroll)
		}
	}
</script>

<style scoped>
	.backBig{
		background: rgba(0,0,0,.5);
		position: absolute;
		top: .2rem;
		left: .2rem;
		z-index: 2;
		width: .6rem;
		height: .6rem;
		color: white;
		text-align: center;
		line-height: .6rem;
		font-weight: bold;
		border-radius: 50%;
	}
	.back{
		color: white;
		font-size: .14rem;
	}
	.header{
		display: flex;
		background: #00bcd4;
		height: .7rem;
		position: fixed;
		top: 0;
		width: 100%;
		z-index: 11;
		font-size: .14rem;
		color: white;
		align-items: center;
		line-height: .7rem;
		padding: 0 .1rem;
	}
	.choseCity{
		flex: 1;
		text-align: center;
		font-size: .24rem;
	}
</style>