<template>
	<div class="cityHeader">
		<router-link class='back' to='/'>
		<span class="iconfont icon-custom-back"></span>
		</router-link>
		<p class="choseCity">城市选择</p>
	</div>
</template>

<script>
	export default{
		name:'cityHeader',
		
	}
</script>

<style scoped>
	.back{
		color: white;
		font-size: .14rem;
	}
	.cityHeader{
		display: flex;
		background: #00bcd4;
		height: .5rem;
		font-size: .14rem;
		color: white;
		align-items: center;
		line-height: .5rem;
		padding: 0 .1rem;
	}
	.choseCity{
		flex: 1;
		text-align: center;
	}
</style>