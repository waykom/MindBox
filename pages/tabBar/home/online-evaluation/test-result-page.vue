<template>
	<view class="container">
		<view class="ttime">
			<view class="time">
				<text>测评时间：2023.07.19 13:30</text>
				<text style="line-height: 25rpx;font-size: 20px;" class="iconfont">&#xe649;</text>
			</view>
		</view>
		<view class="ttitle">
			综合心理健康测评（SCL-90）
		</view>
		<view class="result">
			<view class="rtop">
				<text style="color: orange;font-size: 10px;margin-bottom: 20rpx;">-- 你的测试结果 --</text>
				<text>本次测评获得80分</text>
			</view>
			<view class="des">
				<text>
					Lorem ipsum, dolor sit amet consectetur adipisicing elit. Necessitatibus laudantium id nisi officiis quae est praesentium beatae maxime provident earum? Aliquam deleniti fuga assumenda eveniet velit nihil, autem dolore voluptate.
				</text>
			</view>
			<view class="op">
				<button class="opbtn" plain>再测一次</button>
				<button style="color: #000;background-color: white;" class="opbtn" plain>向心理专家提问</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		onLoad() {
			uni.setNavigationBarTitle({
				title:'测评结果'
			})
		}
	}
</script>

<style lang="less">
.container{
	width: 100%;
	.ttime{
		display: flex;
		justify-content: flex-end;
		height: 100rpx;
		// background-color: #ddd;
		align-items: center;
		font-size: 10px;
		color: #666;
		.time{
			width: 350rpx;
			// background-color: #bfc;
			display: flex;
			justify-content: space-evenly;
		}
	}
	.ttitle{
		height: 110rpx;
		// line-height: 100rpx;
		padding-left: 30rpx;
		// background-color: #ddd;
	}
	.result{
		width: 90%;
		margin: 0 auto;
		.rtop{
			height: 250rpx;
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			// background-color: #ddd;
		}
		.des{
			font-size: 12px;
			line-height: 35rpx;
			color: #666;
		}
		.op{
			height: 300rpx;
			display: flex;
			justify-content: space-evenly;
			align-items: center;
			.opbtn{
				height: 80rpx;
				line-height: 80rpx;
				font-size: 14px;
				border-radius: 20rpx;
				border: 1px solid #ddd;
				background-color: #F3D4B3;
				color: white;
			}
		}
	}
}
</style>
