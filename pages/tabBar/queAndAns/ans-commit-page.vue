<template>
	<view class="container">
		<view class="commit-box">
			<view class="text">
				<text>描述你的问题</text>
			</view>
			<view class="input-box">
				<input class="input-title" type="text" placeholder="标题" />
				<textarea 
					style="font-size: 12px;" 
					class="input-content"
					:maxlength="600"
					:auto-height="true"
					placeholder="咨询内容" />
			</view>
			<view class="commit">
				<text>提交问题</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="less" scoped>
.container{
	width: 100%;
	height: calc(100vh);
	background-color: #EEEEEE;
	.commit-box{
		width: 90%;
		height: 60%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		margin: 0 auto;
		.text{
			height: 80rpx;
		}
		.input-box{
			background-color: #eee;
			font-size: 14px;
			padding: 0 20rpx;
			color:#333;
			.input-title{
				height: 60rpx;
				background-color: #fff;
			}
			.input-content{
				margin-top: 1px;
				background-color: #fff;
				min-height: 450rpx;
				width: 100%;
			}
		}
		.commit{
			height: 100rpx;
			line-height: 100rpx;
			text-align: center;
			width: 80%;
			margin: 0 auto;
			border-radius: 15rpx;
			background-color: #FEE9BC;
			margin-top: 60rpx;
		}
	}
}
</style>
