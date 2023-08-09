<template>
	<view class="container">
		<view class="add">
			<text>添加照片</text>
		</view>
		<view class="acinfo">
			<text>活动信息</text>
		</view>
		<view class="activity">
			<view class="box">
				<view class="name">
					<text>活动标题</text>
				</view>
				<view class="value">
					<input type="text" value="" placeholder="请输入活动标题" />
				</view>
			</view>
			<view class="box">
				<view class="name">
					<text>活动地址</text>
				</view>
				<view class="value">
					<input type="text" value="" placeholder="请输入活动地址" />
				</view>
			</view>
			<view class="box">
				<view class="name">
					<text>活动时间</text>
				</view>
				<view class="value">
					<input type="text" value="" placeholder="请输入活动时间" />
				</view>
			</view>
			<view class="box">
				<view class="name">
					<text>活动人数</text>
				</view>
				<view class="value">
					<input type="text" value="" placeholder="请输入活动人数" />
				</view>
			</view>
			<view class="content">
				<view class="itt">
					<text class="itt">活动详情</text>
				</view>
				<textarea value="" placeholder="请输入活动详情" />
			</view>
			
			<view class="send">
				<text>确认发布</text>
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
.container{
	width: 100%;
	background-color: #F8F9FD;
	.add{
		width: 94%;
		margin: 0 auto;
		height: 400rpx;
		border-radius: 20rpx;
		display: flex;
		justify-content: center;
		align-items: center;
		background-color: #ddd;
	}
	.acinfo{
		width: 96%;
		height: 100rpx;
		line-height: 100rpx;
		font-size: 18px;
		font-weight: 600;
		margin: 0 auto;
	}
	.activity{
		width: 94%;
		margin: 0 auto;
		overflow: hidden;
		border-radius: 20rpx;
		background-color: #fff;
		.box{
			display: flex;
			justify-content: space-between;
			height: 90rpx;
			align-items: center;
			padding-left: 20rpx;
		}
		.content{
			padding-left: 20rpx;
			.itt{
				height: 90rpx;
				line-height: 90rpx;
			}
		}
		.send{
			height: 100rpx;
			background-color: #F6E6F6;
			display: flex;
			align-items: center;
			justify-content: center;	
		}
	}
}
</style>
