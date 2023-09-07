<template>
	<view class="container">
		<view class="available-balance">
			<view class="top">
				<view class="text">
					<text>可用余额（元）</text>
				</view>
				<view class="refund">
					<text>退款</text>
				</view>
			</view>
			<view class="bottom">
				<view class="total">
					<text>1232.12</text>
				</view>
				<view class="top-up">
					<text>立即充值</text>
				</view>
			</view>
		</view>
		<view class="consumption-record">
			<view class="nav-top">
				<view class="record">
					<text>消费记录</text>
				</view>
				<view class="select-time" @click="openSelectTime">
					<text>日期选择</text>
					<text class="iconfont select-time-icon">&#xe63b;</text>
				</view>
			</view>
			<view class="record-box" v-for="i in 10" :key="i">
				<view class="icon">
					<text class="iconfont icon">&#xe60a;</text>
				</view>
				<view class="content">
					<view class="up-content">
						<view class="text">
							<text>充值金额</text>
						</view>
						<view class="amount">
							<text>+ 200</text>
						</view>
					</view>
					<view class="down-content">
						<view class="down-text">
							<text>余额：1273</text>
						</view>
						<view class="date">
							<text>2023-07-27 10:15</text>
						</view>
					</view>
				</view>
			</view>
		</view>
	
		<uni-popup background-color="#fff" ref="popup" type="bottom">
			<view style="height: 80rpx;"></view>
			<inline-calendar @change="handleDateChange"/>
			<view class="popupOption">
				<text>确定</text>
			</view>
		</uni-popup>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
			}
		},
		methods: {
			openSelectTime() {
				this.$refs.popup.open('bottom')
			},
			handleDateChange(options) {
				console.log(options)
			}
		}
	}
</script>

<style lang="less" scoped>
.container{
	width: 100%;
	height: 100vh;
	background-color: #F4F4F4;
	.available-balance{
		width: 94%;
		margin: 0 auto;
		transform: translateY(6%);
		background-color: #fff;
		.top{
			display: flex;
			padding: 0 20rpx;
			height: 100rpx;
			align-items: center;
			justify-content: space-between;
			border-bottom: 1px solid #ddd;
			.text{
				font-weight: 600;
			}
			.refund{
				background-color: #FF0005;
				height: 40rpx;
				width: 90rpx;
				font-size: 12px;
				color: #fff;
				display: flex;
				align-items: center;
				justify-content: center;
				border-radius: 10rpx;
			}
		}
		.bottom{
			display: flex;
			height: 200rpx;
			padding: 0 20rpx;
			align-items: center;
			justify-content: space-between;
			.total{
				font-size: 20px;
				color: #FF0005;
				font-weight: bold;
			}
			.top-up{
				height: 80rpx;
				width: 170rpx;
				display: flex;
				border-radius: 20rpx;
				align-items: center;
				justify-content: center;
				font-size: 14px;
				background-color: #FF0005;
				color: #fff;
			}
		}
	}
	.consumption-record{
		width: 100%;
		height: 100vh;
		box-sizing: border-box;
		padding: 0 40rpx;
		margin-top: 40rpx;
		background-color: #fff;
		.nav-top{
			height: 120rpx;
			display: flex;
			align-items: center;
			justify-content: space-between;
			.select-time{
				height: 55rpx;
				padding: 0 30rpx;
				border-radius: 30rpx;
				font-size: 12px;
				color: #666;
				display: flex;
				align-items: center;
				justify-content: center;
				background-color: #F2F5F7;
				.select-time-icon{
					font-size: 10px;
					padding-top: 15rpx;
					padding-left: 10rpx;
				}
			}
		}
		.record-box{
			display: flex;
			height: 150rpx;
			border-bottom: 1px solid #ddd;
			.icon{
				display: flex;
				align-items: center;
				justify-content: center;
				font-size: 30px;
				color: #6160F6;
			}
			.content{
				flex: 1;
				margin-left: 20rpx;
				font-size: 14px;
				display: flex;
				flex-direction: column;
				align-content: center;
				justify-content: center;
				.amount{
					font-size: 18px;
					font-weight: bold;
				}
				.up-content{
					display: flex;
					align-items: center;
					justify-content: space-between;
				}
				.down-content{
					color: #666;
					font-size: 12px;
					display: flex;
					align-items: center;
					justify-content: space-between;
				}
			}
		}
	}
	.popupOption{
		height: 100rpx;
		width: 60%;
		margin: 50rpx auto;
		background-color: #00A2FF;
		border-radius: 50rpx;
		display: flex;
		color: #fff;
		align-items: center;
		justify-content: center;
	}
}
</style>
