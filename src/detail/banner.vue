<template>
	<div>
		<div class="banner" @click="handleClickBanner">
	      <img class="banner-img" src="http://img1.qunarzz.com/sight/p0/201404/23/04b92c99462687fa1ba45c1b5ba4ad77.jpg_600x330_bf9c4904.jpg"/>
	      <div class="banner-desc">
	        <div class="banner-title">
	          大连圣亚海洋世界(AAAA景区)
	        </div>
	        <div class="banner-number">
	          <span class="iconfont icon-custom-back"></span>
	          2
	        </div>
	      </div>
	    </div>
	    <div class="ticket">
	    	成人票
	    </div>
	    <Gallery @close="handleClickClose" v-show='showGallery'/>
	</div>
</template>

<script>
	import Gallery from './gallery'
	import DetailHeader from './header'
	export default {
		name:'banner',
		components:{
			Gallery,
			DetailHeader
		},
		data(){
			return{
				showGallery:false
			}
		},
		methods:{
			handleClickBanner(){
				this.showGallery=true
			},
			handleClickClose(){
				this.showGallery=false
			}
		}
	}
</script>

<style scoped>
	.banner{
		overflow: hidden;
	    height:3rem;
	    position:relative;
	    }
	.banner-img{
		width:100%;
		height: 3rem;
		}
	.banner-desc{
		position:absolute;
	    left:0;
	    right:0;
	    bottom:0;
	    line-height: .64rem;
	    display:flex;
	    color: #ffffff;
	}
	 .banner-title{
        flex:1;
        font-size: .32rem;
        padding:0 .2rem;
       }
     .banner-number{
        height: .36rem;
        line-height: .36rem;
        padding:0 .3rem;
        margin-top: .14rem;
        background: #000;
        border-radius:.18rem;
        font-size: .24rem;
    }
    .banner-icon{
    	font-size: .24rem;
    }
          
</style>