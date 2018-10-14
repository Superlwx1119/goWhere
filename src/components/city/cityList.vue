<template>
	<div class="cityList">
		<div v-for="(city,key) of cities" :ref='key' :key='key'>
			<h2>{{key}}</h2>
			<p v-for="(item,key) of city"  :ref="key" :key='item.id'>{{item.name}}</p>
		</div>
	</div>
</template>

<script>
	export default{
		name:'cityList',
		props:{
			cities:Object,
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
</style>