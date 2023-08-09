<template>
	<view class="box">
		<view class="left-img">
			<image style="width: 200rpx;height: 200rpx;" src="@/static/images/icon/tabBar/user.png" mode="aspectFit"></image>
		</view>
		<view class="right-content">
			<view class="right-msg">
				<view class="name-grade-area">
					<view class="ngleft">
						<text class="name">张三李</text>
						<text class="ngrade">初级咨询师</text>
					</view>
					<view>
						<text style="font-size: 20px;margin-right: 20rpx;" class="iconfont">&#xe611;</text>
					</view>
				</view>
				<view class="grade">
					<text>上海</text>
					<text style="margin-left: 20rpx;">36岁</text>
				</view>
				<view class="great">
					<view class="great-box">
						<text>人际关系</text>
					</view>
					<view class="great-box">
						<text>人际关系</text>
					</view>
					<view class="great-box">
						<text>人际关系</text>
					</view>
					<view class="great-box">
						<text>人际关系</text>
					</view>
				</view>
				<view class="experience">
					<view class="left">
						<view class="exbox">
							<text>200</text>
							<text>长程个案</text>
						</view>
						<view class="exbox">
							<text>200</text>
							<text>咨询时长</text>
						</view>
						<view class="exbox">
							<text>200</text>
							<text>续单率</text>
						</view>
					</view>
					<view class="right">
						<text><slot>预约</slot></text>
					</view>
				</view>
			</view>
<!-- 			<view class="right-btn">
				<view>
					<button plain class="btn-a btn" hover-class="none">预约</button>
				</view>
				<view>
					<button plain class="btn-b btn" hover-class="none">提问</button>
				</view>
			</view> -->
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
	height: 300rpx;
	margin: 0 auto;
	margin-top: 30rpx;
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
		width: 450rpx;
		flex-direction: column;
		justify-content: space-evenly;
		.right-msg{
			display: flex;
			flex-direction: column;
			font-size: 14px;
			.name-grade-area{
				display: flex;
				align-items: center;
				justify-content: space-between;
				margin-bottom: 10rpx;
				.ngleft{
					display: flex;
					align-items: center;
					.name{
						font-size: 18px;
						font-weight: bold;
						// margin-right: 40rpx;
					}
					.ngrade{
						font-size: 14px;
						margin-left: 10px;
					}
				}
			}
			.grade{
				font-size: 12px;
				color: #666;
			}
			.great{
				height: 60rpx;
				color: #666;
				display: flex;
				justify-content: space-around;
				align-items: center;
				font-size: 10px;
				.great-box{
					height: 35rpx;
					line-height: 35rpx;
					background-color: #F6E6F6;
					border-radius: 20rpx;
					padding: 0 10rpx;
				}
			}
			.experience{
				display: flex;
				height: 80rpx;
				// background-color: #F6E6F6;
				align-items: center;
				justify-content: space-between;
				.left{
					display: flex;
					font-size: 10px;
					.exbox{
						display: flex;
						flex-direction: column;
						justify-content: center;
						align-items: center;
						width: 110rpx;
						// background-color: #F6E6F6;
					}
					.exbox:nth-child(2){
						border-left: 1rpx solid #ddd;
						border-right: 1rpx solid #ddd;
					}
				}
				.right{
					background-color: #F6E6F6;
					border-radius: 10rpx;
					width: 100rpx;
					height: 50rpx;
					display: flex;
					justify-content: center;
					align-items: center;
				}
			}
		}
		.right-btn{
			display: flex;
			justify-content: flex-end;
			.btn{
				width: 130rpx;
				height: 60rpx;
				line-height: 50rpx;
				border-radius: 50rpx;
				border: 2px solid #F3D4B3;
				margin-right: 20rpx;
				font-size: 14px;
			}
			.btn-b{
				background-color: #F3D4B3;
				color: white;
			}
		}
	}
}
</style>
