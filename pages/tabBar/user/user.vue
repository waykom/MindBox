<template>
	<view class="container">
		<view class="head-container">
			<view class="title">
				<text>个人中心</text>
			</view>
			<view class="user-info"  @click="handlerLogin">
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
				<view class="info-item"
					@click="handleClickMyOption(my.to)"
					v-for="my in mainList" :key="my.id"
				>
					<text class="number">{{ my.number }}</text>
					<text>{{ my.name }}</text>
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
				<view 
					class="cart-item"
					@click="handleClickOrderOption(item.id)"
					v-for="item in orderList" :key="item.id"
				>
					<text class="iconfont icon">{{ item.icon }}</text>
					<text class="ctext">{{ item.name }}</text>
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
					@click="onClick(item.id)"
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
	
		<uni-popup ref="popup" type="center">
			<view class="popup">
				<view class="topicon">
					
				</view>
				<view class="service-text">
					<view>
						<text>客服电话</text>
					</view>
					<view style="font-size: 14px;">
						<text>110-110-10001</text>
					</view>
					<view style="font-size: 10px;color: #666;">
						<text>客服24小时在线为您服务，如有需要请拨打</text>
					</view>
				</view>
				<view class="options">
					<view class="call">
						<text>立即拨打</text>
					</view>
					<view class="exit">
						<text>取消</text>
					</view>
				</view>
			</view>
		</uni-popup>
	
	</view>
</template>

<script>
	export default {
		data(){
			return{
				// 主要功能
				mainList:[
					{id:1, name:'我的余额', number:2137, to:'group-one/wodeyue'},
					{id:2, name:'我的预约', number:1, to:'group-one/wodeyuyue'},
					{id:3, name:'我的活动', number:0, to:'group-one/wodehuodong'},
					{id:4, name:'我的收藏', number:9, to:'group-one/wodeshoucang'},
				],
				// 我的订单
				orderList:[
					{id:1,name:'待确认',icon:'\ue613'},
					{id:2,name:'服务中',icon:'\ue644'},
					{id:3,name:'已结束',icon:'\ue607'},
					{id:4,name:'已取消',icon:'\ue647'},
				],
				// 常用功能
				commonUseList:[
					{id:1,name:'我的关注',icon:'\ue694',to:'group-three/guanzhu'},
					{id:2,name:'我的测评',icon:'\ue654',to:'group-three/wodeceping'},
					{id:3,name:'我的提问',icon:'\ue7bf',to:'group-three/wodetiwen'},
					{id:4,name:'我的发布',icon:'\uec09',to:'group-three/wodefabu'},
					{id:5,name:'在线客服',icon:'\uec2e',to:''},
					{id:6,name:'个人信息',icon:'\ue659',to:'group-three/gerenxinxi'},
					{id:7,name:'咨询师入驻',icon:'\ue69c',to:'group-three/zixunshiruzhu'},
					{id:8,name:'条款',icon:'\ue608',to:'group-three/tiaokuan'},
				]
			}
		},
		methods:{
			onClick(id){
				if(id === 5) {
					this.$refs.popup.open('center')
				}
			},
			handlerLogin() {
				uni.navigateTo({
					url: 'test-login'
				})
			},
			handleClickMyOption(path) {
				uni.navigateTo({
					url: path
				})
			},
			handleClickOrderOption(orderId) {
				uni.navigateTo({
					url: 'group-two/order'+'?orderId='+orderId
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
	.popup {
		height: 430rpx;
		width: 500rpx;
		border-radius: 20rpx;
		overflow: hidden;
		background-color: #fff;
		.topicon{
			height: 80rpx;
			background-color: #73DBCC;
		}
		.service-text{
			display: flex;
			flex-direction: column;
			justify-content: space-evenly;
			align-items: center;
			font-size: 12px;
			height: 200rpx;
			// background-color: #ddd;
		}
		.options{
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: space-evenly;
			font-size: 14px;
			.call{
				height: 50rpx;
				width: 240rpx;
				border-radius: 50rpx;
				background-color: #F3D4B3;
				display: flex;
				align-items: center;
				justify-content: center;
			}
			.exit{
				height: 70rpx;
				width: 200rpx;
				display: flex;
				align-items: center;
				justify-content: center;
				color: #F3D4B3;
			}
		}
	}
}
</style>