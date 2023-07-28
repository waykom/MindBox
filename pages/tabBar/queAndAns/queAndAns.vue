<template>
	<view class="container">
		<view class="search">
			<input class="sinput" placeholder="搜索你疑惑的问题">
		</view>
		<view class="hot-topic">
			<view class="title">
				<text>热门话题</text>
			</view>
			<view class="items-list">
				<view class="item-box" v-for="(i,index) in 3" :key="index">
					<view class="img">
						<image style="width: 160rpx;height: 360rpx;" src="../../../static/images/home/ic_02.png" mode="aspectFit"></image>
					</view>
					<view class="content">
						<view class="content-title">
							<text>高频常见问题</text>
						</view>
						<view class="des">
							<text>
								Lorem ipsum dolor sit amet consectetur adipisicing elit. Fugit, velit vero harum corporis quaerat minima distinctio itaque dolore? Cum et possimus, voluptatibus aliquid eveniet voluptatem velit quod quae? Placeat, voluptates!
							</text>
						</view>
						<view class="todo">
							<view class="share">
								<text class="iconfont icon">&#xe623;</text>
								<text>分享</text>
							</view>
							<view class="commit">
								<text class="iconfont icon">&#xe636;</text>
								<text>666</text>
							</view>
							<view class="like">
								<text class="iconfont icon">&#xec7f;</text>
								<text>666</text>
							</view>
						</view>
						<view>
							<button plain class="save">加入话题</button>
						</view>
					</view>
				</view>
			</view>
		</view>
		<ul class="area-list">
			<li v-for="(area,index) in areaList" 
				:key="area.id"
				@click="goArea(index)"
				:class="areaIndex==index ? 'li-active' : ''"
				>
					{{ area.name }}
			</li>
		</ul>
		<view class="discuss-box" v-for="i in 2" :key="i">
			<view class="user">
				<view class="left">
					<view class="head">
						<image style="width: 50rpx;height: 50rpx;" src="../../../static/images/icon/tabBar/user.png" mode="aspectFit"></image>
					</view>
					<view class="phone">
						<text>1564981811</text>
					</view>
				</view>
				<view class="right">
					<button plain>+ 关注</button>
				</view>
			</view>
			<view class="content">
				<text>
					一言有限公司成立于2013年04月19日，注册地位于福建省泉州市晋江市内坑镇上方村群峰路220号13楼，法定代表人为黄小豆。经营范围包括一般项目：以自有资金从事投资活动；货物进出口；技术进出口；进出口代理；国内货物运输代理；非金属矿及制品销售；矿山机械销售；鞋帽零售；鞋制造；矿物洗选加工；选矿；软件开发；科技中介服务；社会经济咨询服务（除依法须经批准的项目外，凭营业执照依法自主开展经营活动）一言有限公司对外投资4家公司。
				</text>
			</view>
			<view class="operation">
				<view>
					<text class="iconfont icon">&#xe623;</text>
					<text>分享</text>
				</view>
				<view>
					<text class="iconfont icon">&#xe636;</text>
					<text>666</text>
				</view>
				<view>
					<text class="iconfont icon">&#xec7f;</text>
					<text>666</text>
				</view>
			</view>
		</view>
		
		<view class="commit-fix">
			<text>提问</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				areaIndex:0,
				areaList:[
					{id:1,name:'推荐'},
					{id:2,name:'社会交际'},
					{id:3,name:'个人成长'},
					{id:4,name:'恋爱情感'},
					{id:5,name:'婚姻家庭'},
					{id:6,name:'婚姻家庭'},
					{id:7,name:'婚姻家庭'},
					{id:8,name:'恋爱情感'},
					{id:9,name:'婚姻家庭'}
				],
			};
		},
		methods: {
			goArea(index){
				this.areaIndex = index
			},
		}
	}
</script>

<style lang="less" scoped>
.container{
	width: 100%;
	.search{
		display: flex;
		justify-content: center;
		margin-top: 20rpx;
		.sinput{
			width: 85%;
			box-sizing: border-box;
			height: 80rpx;
			padding-left: 28%;
			color: #333;
			border-radius: 20rpx;
			background-color: #FAFAFA;
			background-image: url('@/static/images/home/search.png');
			background-repeat: no-repeat;
			background-size: 5%;
			background-position: 25% center;
		}
	}
	.hot-topic {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		justify-content: space-evenly;
		height: 580rpx;
		width: 92%;
		margin: 0 auto;
		.title {
			height: 33rpx;
			margin-left: 10rpx;
			border-radius: 10rpx;
			font-size: 20px;
			font-weight: 600;
			border-bottom: 20rpx solid #F3D4B3;
		}
		.items-list::-webkit-scrollbar{
			display: none;
		}
		.items-list {
			display: flex;
			overflow: auto;
			width: 100%;
			.item-box{
				margin-right: 30rpx;
				flex-shrink: 0;
				display: flex;
				box-sizing: border-box;
				justify-content: space-between;
				width: 600rpx;
				height: 400rpx;
				border-radius: 15rpx;
				border: 2px solid #F3D4B3;
				.img{
					// width: 200rpx;
					background-color: #eee;
					// box-sizing: border-box;
					// padding: 20rpx;
				}
				.content{
					width: 400rpx;
					display: flex;
					flex-direction: column;
					justify-content: space-evenly;
					.content-title {
						margin-top: 20rpx;
						font-size: 18px;
						font-weight: bold;
						margin-left: 30rpx;
					}
					.des{
						height: 160rpx;
						box-sizing: border-box;
						padding-left: 30rpx;
						width: 100%;
						font-size: 14px;
						color: #666;
						text{
							display:-webkit-box;
							-webkit-line-clamp:4;
							-webkit-box-orient:vertical;
							overflow:hidden;
						}
					}
					.todo{
						font-size: 10px;
						justify-content: space-around;
						display: flex;
						color: #444;
						.icon {
							font-size: 12px;
							margin-right: 8rpx;
						}
					}
					.save{
						// width: 150rpx;
						height: 50rpx;
						line-height: 50rpx;
						font-size: 10px;
						font-weight: bold;
						border: none;
						background-color: #F3D4B3;
						margin-left: 200rpx;
						margin-right: 30rpx;
					}
				}
			}
		}
	}	
	.area-list{
		padding: 0;
		margin: 0;
		list-style: none;
		height: 100rpx;
		width: 95%;
		margin: 0 auto;
		// margin-top: 10rpx;
		display: flex;
		overflow: auto;
		align-items: center;
		text-align: center;
		&::-webkit-scrollbar {
			display: none;
		}
		li{
			flex-shrink: 0;
			// width: 150rpx;
			margin: 0 20rpx;
			color: #888;
			font-size: 14px;
			transition: all 0.1s linear;
		}
		.li-active{
			font-size: 20px;
			color: #333;
		}
	}
	.discuss-box{
		display: flex;
		flex-direction: column;
		justify-content: space-around;
		width: 92%;
		margin: 0 auto;
		.user{
			display: flex;
			justify-content: space-between;
			align-items: center;
			height: 90rpx;
			// background-color: #ddd;
			margin-top: 20rpx;
			.left{
				display: flex;
				align-items: center;
				.head{
					width: 70rpx;
					height: 70rpx;
					line-height: 90rpx;
					text-align: center;
					border-radius: 50%;
					background-color: skyblue;
				}
				.phone{
					margin-left: 20rpx;
					font-weight: bold;
					font-size: 14px;
					color: #4d4d4d;
				}
			}
			.right{
				button{
					// width: 120rpx;
					height: 55rpx;
					line-height: 55rpx;
					border-radius: 50rpx;
					font-size: 14px;
					color: #3A72FD;
					border: none;
					background-color: #EEF3FF;
					margin-right: 20rpx;
				}
			}
		}
		.content{
			// background-color: #ddd;
			max-height: 400rpx;
			padding: 10rpx 5rpx;
			color: #333;
			text{
				display:-webkit-box;
				-webkit-line-clamp:8;
				-webkit-box-orient:vertical;
				overflow:hidden;
			}
		}
		.operation{
			display: flex;
			justify-content: space-around;
			align-items: center;
			// background-color: #ddd;
			height: 80rpx;
			margin-top: 20rpx;
			border-top: 1px solid #ddd;
			border-bottom: 10px solid #F7F8FC;
			view{
				display: flex;
				align-items: center;
				text {
					font-size: 10px;
					color: #666;
				}
				.icon{
					margin-right: 10rpx;
					font-size: 16px;
				}
			}
		}
	}
	.commit-fix{
		position: fixed;
		right: 20rpx;
		bottom: 120rpx;
		width: 150rpx;
		height: 150rpx;
		line-height: 150rpx;
		text-align: center;
		border-radius: 50%;
		font-weight: bold;
		color: #666;
		font-size: 20px;
		background-color: #F3D4B3;
		opacity: 0.9;
	}
}
</style>