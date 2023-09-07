<template>
	<view class="container">
		<view class="box" v-for="i in 3" :key="i">
			<view class="status">
				<view class="status-box status-active">
					<text>进行中</text>
				</view>
			</view>
			<view class="leader keyvalue">
				<text class="key">活动名称</text>
				<text class="value">如何培养安全感满满的孩子|父母解忧沙龙</text>
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
		.status{
			height: 60rpx;
			display: flex;
			font-size: 10px;
			color: #fff;
			align-items: flex-end;
			justify-content: flex-end;
			// background-color: #ddd;
			.status-box{
				padding: 2rpx 10rpx;
				transform: translateY(10rpx) translateX(-20rpx);
			}
			.status-active{
				background-color: #F3D4B3;
			}
			.status-disactive{
				background-color: #E5E5E5;
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
				width: 180rpx;
			}
		}
	}
}
</style>
