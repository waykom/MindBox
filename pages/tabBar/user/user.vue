<template>
	<view class="container">
		<view class="head-container">
			<view class="title">
				<text>个人中心</text>
			</view>
			<view class="user-info">
				<view class="img">
					<image style="width: 100rpx;height: 100rpx;" src="@/static/images/icon/tabBar/user.png" mode="aspectFit"></image>
				</view>
				<view class="info">
					<view class="name">
						<text>心事盒助理</text>
					</view>
					<view class="uid">
						<text>1564981811</text>
					</view>
				</view>
			</view>
			<view class="o-info">
				<view class="info-item">
					<text class="number">2173</text>
					<text>我的余额</text>
				</view>
				<view class="info-item">
					<text class="number">1</text>
					<text>我的预约</text>
				</view>
				<view class="info-item">
					<text class="number">0</text>
					<text>我的活动</text>
				</view>
				<view class="info-item">
					<text class="number">9</text>
					<text>我的收藏</text>
				</view>
			</view>
		</view>
		<view style="height: 100rpx;"></view>
		<view class="order-cart">
			<view class="cart-head">
				<view class="left">
					<text>我的订单</text>
				</view>
				<view class="right">
					<text>查看全部订单 ></text>
				</view>
			</view>
			<view class="cart-content">
				<view class="cart-item">
					<text class="iconfont icon">&#xe63a;</text>
					<text class="ctext">全部</text>
				</view>
				<view class="cart-item">
					<text class="iconfont icon">&#xe613;</text>
					<text class="ctext">待确认</text>
				</view>
				<view class="cart-item">
					<text class="iconfont icon">&#xe644;</text>
					<text class="ctext">服务中</text>
				</view>
				<view class="cart-item">
					<text class="iconfont icon">&#xe607;</text>
					<text class="ctext">已结束</text>
				</view>
				<view class="cart-item">
					<text class="iconfont icon">&#xe647;</text>
					<text class="ctext">已取消</text>
				</view>
			</view>
		</view>
	
		<view class="job-list">
			<view style="font-size: 12px;margin-top: 20rpx;margin-left: 20rpx;">
				<text>常用功能</text>
			</view>
			<uni-list :border="false" style="margin-top: 10rpx;">
				<uni-list-item
					class="list-item"
					:border="false"
					showArrow
					clickable
					:to="item.to"
					@click="onClick"
					v-for="item in commonUseList" :key="item.id">
					<template #header>
						<view class="slot-box-header">
							<!-- <image class="slot-image" style="width: 50rpx;height: 50rpx;" src="@/static/images/icon/tabBar/user.png" mode="aspectFit"></image> -->
							<text class="iconfont icon">{{ item.icon }}</text>
						</view>
					</template>
					<template #body>
						<view class="slot-box-body">
							<text class="slot-text">{{ item.name }}</text>
						</view>
					</template>
				</uni-list-item>
			</uni-list>
		</view>
	</view>
</template>

<script>
	export default {
		data(){
			return{
				// 常用功能
				commonUseList:[
					{id:1,name:'我的关注',icon:'\uec7f',to:''},
					{id:2,name:'我的测评',icon:'\uec7f',to:''},
					{id:3,name:'我的提问',icon:'\uec7f',to:''},
					{id:4,name:'我的发布',icon:'\uec7f',to:''},
					{id:5,name:'在线客服',icon:'\uec7f',to:''},
					{id:6,name:'个人信息',icon:'\uec7f',to:''},
					{id:7,name:'咨询师入驻',icon:'\uec7f',to:''},
					{id:8,name:'条款',icon:'\uec7f',to:''},
				]
			}
		},
		methods:{
			onClick(e){
				console.log('jjjj',e)
				uni.showToast({
					title:'点击反馈'
				})
			}
		}
	}
</script>

<style lang="less" scoped>
.container{
	width: 100%;
	// height: 2500rpx;
	background-color: #FEFEF8;
	.head-container{
		display: flex;
		flex-direction: column;
		height: 380rpx;
		background-color: #F6E4F6;
		.title{
			height: 100rpx;
			line-height: 100rpx;
			text-align: center;
			// background-color: #ddd;
		}
		.user-info{
			height: 200rpx;
			flex-shrink: 0;
			// background-color: #ddd;
			display: flex;
			align-items: center;
			width: 85%;
			margin: 0 auto;
			.img{
				width: 150rpx;
				height: 150rpx;
				line-height: 215rpx;
				background-color: #fff;
				border-radius: 50%;
				text-align: center;
			}
			.info{
				margin-left: 30rpx;
				display: flex;
				flex-direction: column;
				// background-color: red;
				height: 100rpx;
				justify-content: space-between;
				.name{
					font-size: 18px;
				}
				.uid{
					font-size: 14px;
				}
			}
		}
		.o-info{
			flex-shrink: 0;
			height: 150rpx;
			width: 94%;
			margin: 0 auto;
			margin-top: 30rpx;
			background-color: #fff;
			border-radius: 30rpx;
			display: flex;
			justify-content: space-around;
			// border: 1px solid #ddd;
			font-size: 14px;
			.info-item{
				display: flex;
				// background-color: #bfc;
				flex-direction: column;
				justify-content: center;
				align-items: center;
				.number{
					color: red;
				}
			}
		}
	}
	.order-cart{
		display: flex;
		flex-direction: column;
		justify-content: space-evenly;
		width: 94%;
		margin: 0 auto;
		margin-top: 30rpx;
		border-radius: 30rpx;
		height: 180rpx;
		// border: 1px solid #ddd;
		background-color: #fff;
		.cart-head{
			display: flex;
			justify-content: space-between;
			align-items: center;
			width: 94%;
			margin: 0rpx auto;
			.left{
				font-size: 12px;
			}
			.right{
				font-size: 10px;
			}
		}
		.cart-content{
			display: flex;
			justify-content: space-evenly;
			// margin-bottom: 8rpx;
			.cart-item{
				display: flex;
				flex-direction: column;
				align-items: center;
				justify-content: space-around;
				.icon{
					font-size: 25px;
				}
				.ctext{
					font-size: 12px;
				}
			}
		}
	}
	
	.job-list{
		width: 94%;
		margin: 0 auto;
		margin-top: 50rpx;
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		// height: 300rpx;
		padding-bottom: 50rpx;
		// background-color: #ddd;
		// border: 1px solid #ddd;
		// height: 600rpx;
		border-radius: 30rpx;
		background-color: #fff;
		.list-item{
			height: 140rpx;
			.slot-box-header{
				display: flex;
				justify-content: center;
				align-items: center;
				width: 80rpx;
				height: 80rpx;
				// background-color: #ddd;
				.icon{
					font-size: 20px;
				}
			}
			.slot-box-body{
				display: flex;
				justify-content: center;
				align-items: center;
				font-size: 14px;
				color: #000;
				margin-left: 30rpx;
			}
		}
	}
}
</style>