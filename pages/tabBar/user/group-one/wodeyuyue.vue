<template>
	<view class="container">
		<view class="box">
			<view class="title">
				<text class="iconfont icon">&#xe664;</text>
				<text>心理咨询师预约</text>
			</view>
			<view class="leader keyvalue">
				<text class="key">预约咨询师</text>
				<text class="value">李四</text>
			</view>
			<view class="user keyvalue">
				<text class="key">预约人</text>
				<text class="value">李四</text>
			</view>
			<view class="time keyvalue">
				<text class="key">预约时间</text>
				<text class="value">2023-07-12</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="less" scoped>
.container{
	width: 100%;
	height: 100vh;
	background-color: #F8F8F8;
	// display: flex;
	// flex-direction: column-reverse;
	.box{
		width: 94%;
		border-radius: 10rpx;
		margin: 0rpx auto;
		margin-bottom: 20rpx;
		transform: translateY(20rpx);
		background-color: #fff;
		padding-left: 40rpx;
		padding-bottom: 50rpx;
		box-sizing: border-box;
		.title{
			height: 100rpx;
			display: flex;
			align-items: center;
			font-weight: 600;
			.icon{
				font-size: 20px;
				color: #F3D4B3;
				margin-right: 20rpx;
			}
		}
		.keyvalue{
			display: flex;
			align-items: center;
			font-size: 12px;
			line-height: 60rpx;
			padding-left: 20rpx;
			.key{
				color: #666;
				width: 200rpx;
				
			}
		}
	}
}
</style>
