<template>
	<view class="box">
		<view class="left-img">
			<image style="width: 200rpx;height: 200rpx;" src="../../static/images/icon/tabBar/user.png" mode="aspectFit"></image>
		</view>
		<view class="right-content">
			<view class="right-msg">
				<view class="name-grade">
					<view>
						<text class="name">张三</text>
					</view>
					<view>
						<text class="grade">初级咨询师</text>
					</view>
				</view>
				<view class="grade">
					<text>国家一级心理咨询师</text>
				</view>
				<view class="great">
					<text>擅长：人际关系、成长问题</text>
				</view>
				<view class="experience">
					<text>从业三年</text>
				</view>
			</view>
			<view class="right-btn">
				<view>
					<button plain class="btn-a" hover-class="none">预约</button>
				</view>
				<view>
					<button plain class="btn-b" hover-class="none">提问</button>
				</view>
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
.box{
	width: 97%;
	height: 350rpx;
	margin: 0 auto;
	margin-top: 50rpx;
	border-radius: 20rpx;
	box-shadow: 0px 0px 10px #ccc;
	display: flex;
	justify-content: space-around;
	align-items: center;
	.left-img{
		background-color: #ddd;
		width: 250rpx;
		height: 250rpx;
		line-height: 400rpx;
		border-radius: 50%;
		text-align: center;
	}
	.right-content{
		display: flex;
		height: 100%;
		flex-direction: column;
		justify-content: space-evenly;
		.right-msg{
			display: flex;
			flex-direction: column;
			font-size: 14px;
			.name-grade{
				display: flex;
				align-items: center;
				margin-bottom: 10rpx;
				.name{
					font-size: 18px;
					font-weight: bold;
					margin-right: 40rpx;
				}
			}
			.grade{
			}
			.great{
				color: #666;
			}
			.experience{
				color: #666;
			}
		}
		.right-btn{
			display: flex;
			justify-content: flex-end;
			button{
				width: 130rpx;
				height: 60rpx;
				line-height: 50rpx;
				border-radius: 50rpx;
				border: 2px solid #079D6C;
				margin-right: 20rpx;
				font-size: 14px;
			}
			.btn-b{
				background-color: #079D6C;
				color: white;
			}
		}
	}
}
</style>
