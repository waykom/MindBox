<template>
	<view>
		<template>
			<slot name="dateSlot"></slot>
		</template>
		<view class="emo-container">
			<template>
				<view class="emo-item" v-for="title in list" :key="title.id">
					<view class="top">
						<text>{{ title.title }}</text>
					</view>
					<view class="bottom">
						<view class="item" v-for="item in title.items" :key="item.id">
							<button class="btn" :class="{'active':item.isActive}" @click="handleTypeBtn(item)" plain>{{ item.name }}</button>
						</view>
					</view>
				</view>
			</template>
			<view class="emo-btns">
				<button class="bts-left btn" plain>重置</button>
				<button class="bts-right btn" @click="handleConfirm" plain>确认</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"filter-item",
		props:{
			filterItemList:{
				type: Array,
				default: [
					{
						id:1,
						title:'情绪管理',
						items:[
							{ id:1, name:'全部', isActive:false},
							{ id:2, name:'情绪失控', isActive:false},
							{ id:3, name:'性格不合', isActive:false},
							{ id:4, name:'孤独', isActive:false},
							{ id:5, name:'情绪不稳定', isActive:false},
							{ id:6, name:'焦虑', isActive:false},
							{ id:7, name:'抑郁', isActive:false},
						]
					}
				]
			}
		},
		data() {
			return {
				list:undefined
			};
		},
		mounted(){
			this.list = this.filterItemList
			// console.log(this.list)
		},
		methods:{
			// 处理筛选按钮
			handleTypeBtn(item) {
				item.isActive = !item.isActive
			},
			// 确认按钮
			handleConfirm() {
				console.log(this.list)
			}
		}
	}
</script>

<style lang="less" scoped>
.emo-container{
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: space-between;
	.emo-item{
		width: 90%;
		display: flex;
		flex-direction: column;
		margin-top: 40rpx;
		.top {
			font-size: 18px;
		}
		.bottom{
			background-color: #fff;
			display: flex;
			
			flex-wrap: wrap;
			margin-top: 30rpx;
			justify-content: flex-start;
			align-items: center;
			.item {
				display: flex;
				align-items: center;
				height: 50rpx;
				// background-color: #ddd;
				margin: 10rpx;
				.btn {
					// width: 130rpx;
					height: 50rpx;
					// margin-right: 40rpx;
					margin-bottom: 30rpx;
					line-height: 50rpx;
					border-radius: 25rpx;
					background-color: #F1F4F5;
					border: none;
					font-size: 14px;
					color: #666;
				}
				.active{
					background-color: #F3D4B3;
				}
			}

		}
	}
	.emo-btns{
		display: flex;
		width: 92%;
		margin-bottom: 20rpx;
		margin-top: 50rpx;
		.btn{
			width: 300rpx;
			height: 80rpx;
			line-height: 80rpx;
			border-radius: 10rpx;
			background-color: #F1F4F5;
			border: none;
			color: #333;
		}
		.bts-right{
			background-color: #F3D4B3;
		}
	}
}
</style>