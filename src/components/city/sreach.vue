<template>
	<div class="srcach">
		<div>
			<input type="text" v-model="keyword" class="search_inp" placeholder="输入城市名或拼音" />
		</div>
		<div class="search-conent" v-show="keyword" ref="search">
	      <ul>
	        <li
	          class="search-item"
	          v-for="item of list"
	          :key="item.id"
	          @click="handleClickCity(item.name)"
	        >
	          {{item.name}}
	        </li>
	        <li class="search-item" v-show="!list.length">没有找到数据</li>
	      </ul>
	    </div>
	</div>
	
</template>

<script>
	import BScroll from 'better-scroll'
	export default{
		name:'sreach',
	    props: {
		    cities: Object
		  },
		  data () {
		    return {
		      keyword: '',
		      list: [],
		      timer: null
		    }
		  },
		  methods: {
		    handleClickCity (city) {
		      this.$store.dispatch('changeCity', city)
		      this.$router.push('/')
		    }
		  },
		  mounted () {
		    this.scroll = new BScroll(this.$refs.search)
		  },
		  watch: {
		    keyword () {
		      if (this.timer) {
		        clearInterval(this.timer)
		      }
		      if (!this.keyword) {
		        this.list = []
		        return
		      }
		      this.timer = setTimeout(() => {
		        const result = []
		        for (let i in this.cities) {
		          this.cities[i].forEach((value) => {
		            if (value.spell.indexOf(this.keyword) > -1 || value.name.indexOf(this.keyword) > -1) {
		              result.push(value)
		            }
		          })
		        }
		        this.list = result
		      }, 100)
		    }
		  }
	}
</script>

<style scoped>
	.srcach{
		display: flex;
		height: .7rem;
		align-items: center;
		justify-content: center;
		background: #00bcd4;
		padding: 0 .2rem;
	}
	.srcach input{
		height: .5rem;
		width: 6rem;
		text-align: center;
		color: #757575;
		border-radius: 5px;
		border: none;
	}
	.search-conent{
		overflow: hidden;
	    position: absolute;
	    top: 1.2rem;
	    left:0;
	    right:0;
	    bottom:0;
	    background: #eee;
	    z-index:99;
	}
	.search-item{
		line-height: .62rem;
	    padding-left: .2rem;
	    background: #ffffff;
	}
</style>