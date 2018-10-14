<template>
	<div class="hot">
		<h2>周末去哪玩</h2>
		<div class="hot-list">
	      <div class="list-item" v-for="item of weekendList" :key='item.id'>
	        <img class="item-img" :src="item.imgUrl"/>
	        <div class="item-right">
	          <div class="item-title">{{item.title}}</div>
	          <div class="item-desc">{{item.desc}}</div>
	        </div>
	      </div>
		</div>
	</div>
</template>

<script>
	export default{
		name:'Hot',
		props:{
			weekendList:Array
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
		margin-left: .1rem;
	}
	.list-item{
		border-bottom: 1px solid gainsboro;
	}
	.item-img{
		width: 100%;
		height: 2.5rem;
	}
	.item-title{
		font-size: .26rem;
		color: black;
		margin-top: .1rem;
	}
	.item-desc{
		font-size: .22rem;
		color: #cccccc;
		line-height: .35rem;
	}
	.item-btn{
		background: #ff9300;
		border: none;
		color: white;
		padding: .1rem .2rem;
		margin-top: .2rem;
	}
</style>