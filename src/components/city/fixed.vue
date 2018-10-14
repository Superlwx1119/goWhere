<template>
	<div class="fixed">
		<div v-for="(city,key) of cities" :ref='key' :key='key'>
			<p @click="handleClickBetter"  @touchstart="handleTouchstart" @touchmove="handleTouchmove" @touchend="handleTouchend">{{key}}</p>
		</div>
	</div>
</template>

<script>
	export default{
		name:'fixed',
		data(){
			return{
				 touchStatus: false,
     			 timer: null
			}
		},
		computed: {
		    letters () {
		      const letters = []
		      for (let i in this.cities) {
		        letters.push(i)
		      }
		      return letters
		    }
		},
		props:{
			cities:Object,
			better:String
		},
		methods:{
			handleClickBetter(e){
				this.$emit('change', e.target.innerText)
				console.log(e.target.innerText)
			},
			handleTouchstart(){
				this.touchStatus=true
			},
			handleTouchmove(e){
				if(this.touchStatus){
					 const touchY = e.targetTouches[0].clientY
			          const startY = this.$refs['A'][0].offsetTop
			           console.log(startY)
			          const index = Math.floor((touchY - startY) / 40)
			          console.log(this.letters[index])
				}
			},
			handleTouchend(){
				this.touchStatus=false
			}
		}
	}
</script>

<style scoped>
	.fixed p{
		line-height: .4rem;
	}
	.fixed{
		position: absolute;
		right: 0;
		top: 0;
		bottom: 0;
		width: .3rem;
		display: flex;
		margin-right: .1rem;
		margin-top: 3rem;
		align-items: center;
		flex-direction: column;
		justify-content: center;
		color: #17c2d7;
		height: 7rem;
	}
</style>