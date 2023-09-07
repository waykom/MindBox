<template>
	<view class="container">
		<view class="box" v-for="i in 3" :key="i">
			<view class="title">
				<text>
					这是一个问题
				</text>
			</view>
			<view class="des">
				<text>本问题由心理专家丽丽为你解答</text>
				<text>2023-07-27 15:11</text>
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
	padding-top: 60rpx;
	.box{
		width: 94%;
		margin: 10rpx auto;
		border-bottom: 1px solid #ddd;
		padding: 0 3%;
		.title{
			height: 80rpx;
			display: flex;
			align-items: center;
			font-weight: 600;
		}
		.des{
			padding-bottom: 10rpx;
			display: flex;
			align-items: center;
			justify-content: space-between;
			font-size: 10px;
			color: #666;
		}
	}
}
</style>
