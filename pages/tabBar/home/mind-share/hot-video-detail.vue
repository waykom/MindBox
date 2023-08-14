<template>
	<view class="container">
		<view>
			<video 
				class="video"
				src="https://qiniu-web-assets.dcloud.net.cn/unidoc/zh/2minute-demo.mp4"
				
				controls></video>
		</view>
		
		<view class="main-info">
			<view class="user">
				<view class="profile">
					<!-- 90 -->
				</view>
				<view class="name">
					<text>鸣人</text>
				</view>
				<view class="asn">
					<text class="iconfont">&#xe603;</text>
				</view>
			</view>
			<view class="title">
				<text>医护人员对患者的照顾有多细心？</text>
			</view>
			<view class="time">
				<text>2020/02/25</text>
				<text style="font-size: 10px;margin-left: 20rpx;padding-top: 3rpx;margin-right: 2rpx;" class="iconfont">&#xe62c;</text>
				<text>23w</text>
			</view>
			<view class="desc">
				<text>跟随急着镜头去看一看，他们真的不容易</text>
			</view>
			<view class="icon">
				<view class="icon-box">
					<text class="iconfont myic">&#xec7f;</text>
					<text class="icontext">12w</text>
				</view>
				<view class="icon-box">
					<text class="iconfont myic">&#xec7f;</text>
					<text class="icontext">不喜欢</text>
				</view>
				<view class="icon-box">
					<text class="iconfont myic">&#xec7f;</text>
					<text class="icontext">12w</text>
				</view>
				<view class="icon-box">
					<text class="iconfont myic">&#xec7f;</text>
					<text class="icontext">565</text>
				</view>
			</view>
		</view>
		
		<review-container></review-container>
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
	.video{
		width: 100%;
		height: 400rpx;
	}
	.main-info{
		width: 90%;
		margin: 0 auto;
		.user{
			height: 100rpx;
			// background-color: #ddd;
			display: flex;
			align-items: center;
			justify-content: space-between;
			.profile{
				width: 90rpx;
				height: 90rpx;
				border-radius: 50%;
				background-color: #bfc;
			}
			.name{
				flex: 1;
				font-size: 14px;
				margin-left: 20rpx;
			}
			.asn{
				color: #666;
			}
		}
		.title{
			font-size: 16px;
		}
		.time{
			font-size: 10px;
			height: 40rpx;
			color: #666;
			display: flex;
			align-items: center;
		}
		.desc{
			font-size: 12px;
			color: #333;
		}
		.icon{
			width: 90%;
			margin: 0 auto;
			display: flex;
			align-items: center;
			justify-content: space-between;
			height: 150rpx;
			.icon-box{
				display: flex;
				flex-direction: column;
				align-items: center;
				color: #333;
				.myic{
					font-size: 22px;
				}
				.icontext{
					font-size: 10px;
				}
			}
		}
	}
}
</style>
