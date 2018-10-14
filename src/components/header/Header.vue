<template>
	<div class="header">
		<span class="iconfont icon-custom-back"></span>
		<div class="iconfont" type="text"><span class="search">&#xe62b;</span>输入城市/景点/游玩主题</div>
		<p>
			<router-link  class='header-city' to='/city'>
			<span>{{this.$store.state.city}}</span><span class="iconfont icon-htmal5icon03"></span>
			</router-link>
		</p>
	</div>
</template>

<script>
	export default{
		name:'Header',
		props:{
			city:String
		}
	}
</script>

<style>
	.header{
		display: flex;
		background: #00bcd4;
		height: .5rem;
		font-size: .14rem;
		color: white;
		align-items: center;
		line-height: .5rem;
		justify-content: space-between;
		padding: 0 .1rem;
	}
	.header div{
		background: white;
		color: #d5ccd2;
		font-size: .14rem;
		border-radius: .1rem;
		border: none;
		outline: none;
		height: .35rem;
		width: 4.5rem;
		line-height: .35rem;
		align-items: center;
	}
	.header-city{
		color: white;
		padding-right: .1rem;
	}
	.search{
		font-size: .24rem;
	}
</style>