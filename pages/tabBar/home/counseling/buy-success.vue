<template>
	<view class="main">
		<view class="img">
			
		</view>
		<view class="text">
			<view class="title">
				<text>恭喜您，预约成功！</text>
			</view>
			<view class="ttext">
				<text>
					您的心事盒咨询师尽快与您联系，请耐心等特，24小时在线服务。以下是您的预约信息。
				</text>
			</view>
		</view>
		<view class="info">
			<view class="info-row">
				<view class="name">
					<text>预约课程</text>
				</view>
				<view class="value">
					<text>重新定义你的人生</text>
				</view>
			</view>
			<view class="info-row">
				<view class="name">
					<text>预约类别</text>
				</view>
				<view class="value">
					<text>视频咨询</text>
				</view>
			</view>
			<view class="info-row">
				<view class="name">
					<text>联系人</text>
				</view>
				<view class="value">
					<text>丽丽</text>
				</view>
			</view>
			<view class="info-row">
				<view class="name">
					<text>联系方式</text>
				</view>
				<view class="value">
					<text>1564981811</text>
				</view>
			</view>
			<view class="info-row">
				<view class="name">
					<text>预约时间</text>
				</view>
				<view class="value">
					<text>{{new Date().toLocaleString()}}</text>
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

<style lang="less">
	.main{
		width: 100%;
		background-color: #FAFAFA;
		.img{
			width: 100%;
			height: 450rpx;
			display: flex;
			align-items: center;
			justify-content: center;
			background-color: #bfc;
		}
		.text{
			width: 94%;
			margin: 0 auto;
			display: flex;
			flex-direction: column;
			height: 250rpx;
			align-items: center;
			justify-content: space-evenly;
			.title{
				font-size: 18px;
				font-weight: 600;
			}
			.ttext{
				font-size: 12px;
				text-align: center;
				color: #666;
			}
		}
		.info{
			width: 90%;
			height: 500rpx;
			background-color: #fff;
			margin: 0 auto;
			padding: 50rpx;
			box-sizing: border-box;
			.info-row{
				display: flex;
				height: 60rpx;
				line-height: 60rpx;
				font-size: 13px;
				// background-color: #ddd;
				justify-content: space-between;
				.name{
					color: #666;
				}
			}
		}
	}
</style>
