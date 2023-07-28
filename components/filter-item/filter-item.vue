<template>
	<view>
		<view class="emo-container">
			<view class="emo-item" v-for="title in filterItemList" :key="title.id">
				<view class="top">
					<text>{{ title.title }}</text>
				</view>
				<view class="bottom">
					<view class="item" v-for="item in title.items" :key="item.id">
						<button plain>{{ item.name }}</button>
					</view>
				</view>
			</view>
			<view class="emo-btns">
				<button class="bts-left" plain>重置</button>
				<button class="bts-right" plain>确认</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"filter-item",
		data() {
			return {
				filterItemList:[
					{
						id:1,
						title:'类型标题',
						items:[
							{ id:1, name:'类型一'},
							{ id:2, name:'类型二'},
							{ id:3, name:'类型三'},
							{ id:4, name:'类型四'},
							{ id:5, name:'类型五'},
							{ id:6, name:'类型六'},
							{ id:7, name:'类型七'},
						]
					}
				]
			};
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
			button {
				// width: 130rpx;
				height: 50rpx;
				margin-right: 40rpx;
				margin-bottom: 30rpx;
				line-height: 50rpx;
				border-radius: 25rpx;
				background-color: #F1F4F5;
				border: none;
				font-size: 14px;
				color: #666;
			}
		}
	}
	.emo-btns{
		display: flex;
		width: 92%;
		margin-bottom: 20rpx;
		margin-top: 100rpx;
		button{
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