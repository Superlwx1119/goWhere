<template>
	<div class="hot">
		<h2>热销推荐</h2>
		<div class="hot-list">
			<div class="list-item" v-for="item of recommendList" :key='item.id'>
				<router-link :to="'/detail/'+ item.id">
			        <img class="item-img" :src="item.imgUrl"/>
			        <div class="item-right">
			          <div class="item-title">{{item.title}}</div>
			          <div class="item-desc">{{item.desc}}</div>
			          <button class="item-btn">查看详情</button>
			        </div>
	     	   </router-link>
	      	</div>
	      
		</div>
	</div>
</template>

<script>
	export default{
		name:'Hot',
		props:{
			recommendList:Array
		}
	}
</script>

<style scoped="scoped">
	h2{
		height: .6rem;
		background: #eeeeee;
		font-size: .26rem;
		padding-left: .2rem;
		line-height: .6rem;
	}
	.item-right{
		margin-left: .2rem;
	}
	.list-item a{
		display: flex;
		padding: .1rem;
		border-bottom: 1px solid gainsboro;
	}
	.item-img{
		width: 1.6rem;
		height: 1.6rem;
	}
	.item-title{
		font-size: .26rem;
		color: black;
		margin-top: .1rem;
	}
	.item-desc{
		font-size: .22rem;
		color: #cccccc;
		
	}
	.item-btn{
		background: #ff9300;
		border: none;
		color: white;
		padding: .1rem .2rem;
		margin-top: .2rem;
	}
</style>