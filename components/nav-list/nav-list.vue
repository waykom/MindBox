<template>
	<ul class="item-list">
		<li 
			class="lis"
			v-for="(item,index) in navList" 
			:key="item.id"
			@click="goItem(item,index)"
			:class="{'li-active':navIndex===index}"
			>
				{{ item.name }}
		</li>
	</ul>
</template>

<script>
	export default {
		name:"nav-list",
		props:{
			itemList:{
				type:Array,
				default:[
					{id:1,name:'推荐'},
					{id:2,name:'社会交际'},
					{id:3,name:'个人成长'},
					{id:4,name:'恋爱情感'},
					{id:5,name:'婚姻家庭'},
					{id:6,name:'婚姻家庭'},
					{id:7,name:'婚姻家庭'},
					{id:8,name:'恋爱情感'},
					{id:9,name:'婚姻家庭'}
				]
			}
		},
		data() {
			return {
				navIndex:0,
				navList:undefined
			};
		},
		methods: {
			goItem(item,index){
				this.navIndex = index
				this.$emit('change',item)
			},
		},
		watch:{
			// 实时监听父组件传过来的值
			itemList:{
				deep:true,
				immediate:true,
				handler(){
					this.navIndex = 0
					this.navList = this.itemList
				}
			}
		}
	}
</script>

<style lang="less">
	.item-list{
		padding: 0;
		margin: 0;
		list-style: none;
		height: 100rpx;
		width: 95%;
		margin: 0 auto;
		// margin-top: 10rpx;
		display: flex;
		overflow: auto;
		align-items: center;
		text-align: center;
		&::-webkit-scrollbar {
			display: none;
		}
		.lis{
			flex-shrink: 0;
			// width: 150rpx;
			margin: 0 20rpx;
			color: #888;
			font-size: 14px;
			transition: all 0.1s linear;
		}
		.li-active{
			font-size: 20px;
			color: #333;
		}
	}
</style>