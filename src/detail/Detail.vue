<template>
	<div >
		<DetailHeader/>
		<Banner/>
		<div class="content"></div>
	</div>
</template>

<script>
	import DetailHeader from './header'
	import Banner from './banner'
	export default{
		name:'detail',
		components:{
			Banner,
			DetailHeader
		}
	}
</script>

<style scoped>
	.content{
		height: 30rem;
	}
</style>