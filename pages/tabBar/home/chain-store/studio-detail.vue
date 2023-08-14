<template>
	<view class="container">
		<view class="img">
			
		</view>
		<view class="main1">
			<view class="studio-name">
				<text>深圳福田区心理工作室</text>
			</view>
			<view class="worktime">
				<text>周一至周五</text>
				<text>9：00-12：00</text>
				<text>14：00-18：00</text>
			</view>
			<view class="contact-box">
				<view class="text">
					<text>咨询了解</text>
					<text>12666265</text>
				</view>
				<view class="icon">
					<text class="iconfont">&#xe610;</text>
				</view>
			</view>
			<view class="contact-box">
				<view class="text">
						<text>福田区高新南一道9号中科大厦501</text>
					</view>
					<view class="icon">
						<text class="iconfont">&#xe643;</text>
					</view>
				</view>
			</view>
			<view class="main2">
				<view class="nav-fixed">
					<view class="nav-box" 
						v-for="item in navList" 
						@click="handlerClickNav(item.id)"
						:class="navIndex == item.id ? 'nav-box-avtive' : ''"
						:key="item.id">
						<text>{{item.name}}</text>
					</view>
				</view>
			</view>
			<view class="router-view">
				<template v-if="navIndex == 1">
					<view class="introduce">
						<text>
							相处是一种艺术，需要我们用心去经营和维护。当你遇到那个值得你去爱的人时，要学会相互尊重和关注对方的感受包容对方的缺点和不足，同时也要有勇气去表达自己的需要和欲望。在相处中，要学会放下过去的不快和争执，把重点放在未来，共同创造一个充满爱和温暖的未来。每一次争执和挫折都是一次成长和学习的机会，它们可以让我们更加了解对方，更加深入地理解和爱着对方。相处需要耐心和努力，但是它也是一件充满幸福和美好的事情。让我们一起用爱和关心，创造一个充满温暖和亲密的关系。
						</text>
					</view>
				</template>
				<template v-else-if="navIndex == 2">
					<view>
						<consultant></consultant>
					</view>
				</template>
				<template v-else-if="navIndex == 3">
					<view 
						class="course-box" 
						v-for="i in 3" :key="i" 
						@click="goDetail">
						<view class="c-left">
							<image style="width: 200rpx;height: 230rpx;" src="@/static/images/home/ic_02.png" mode="aspectFit"></image>
						</view>
						<view class="c-right">
							<view class="c-title">
								<text>
									重新定义你的认识 | 欧文亚龙团体05期
								</text>
							</view>
							<view class="c-dec">
								<text>8人小组，8月8日起，每周二晚19：00开始讲课，敬请期待！	</text>
							</view>
							<view class="c-info">
								<text style="color: #666;">
									<text class="iconfont">&#xe634;</text>
									<text>广州</text>
								</text>
								<text>
									<text style="color: red;">￥6666/人</text>
								</text>
							</view>
						</view>
					</view>
				</template>
				<template v-else>
					<view style="width: 92%;margin: 0 auto;">
						<view class="li-box" v-for="i in 3" :key="i">
							<view class="li-img-container">
								<!-- 
								width: 230rpx;
								height: 200rpx;
								 -->
							</view>
							<view class="li-content">
								<view class="li-title">
									<text>如何让孩子更有安全感 | 父母解忧沙龙</text>
								</view>
								<view class="li-time">
									<text class="mon lf">7月21日</text>
									<text class="week lf">周五</text>
									<text class="hour lf">9：00-18：00</text>
								</view>
								<view class="li-area">
									<view>
										<text>深圳</text>
									</view>
									<view>
										<text style="color: red;">￥120/人</text>
									</view>
								</view>
							</view>
						</view>
					</view>
				</template>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				navIndex: 1,
				navList:[
					{id:1,name:'工作室介绍'},
					{id:2,name:'心理咨询师'},
					{id:3,name:'课程'},
					{id:4,name:'趣味沙龙'},
				]
			};
		},
		methods:{
			handlerClickNav(id){
				this.navIndex = id
			},
			goDetail() {
				console.log(1)
			}
		}
	}
</script>

<style lang="less" scoped>
.container{
	width: 100%;
	.img{
		height: 480rpx;
		background-color: #bfc;
	}
	.main1{
		width: 90%;
		margin: 0 auto;
		.studio-name{
			font-size: 16px;
			font-weight: bold;
			margin-top: 30rpx;
		}
		.worktime{
			font-size: 10px;
			margin: 6px 0 10px 0;
			color: #666;
			
		}
		.contact-box{
			color: #555;
			font-size: 12px;
			display: flex;
			justify-content: space-between;
			margin-top: 4px;
			.icon{
				width: 100rpx;
				// background-color: #bfc;
				text-align: center;
				color: #F3D4B3;
				border-left: 1px solid #F3D4B3;
			}
		}
	}
	.main2{
		width: 90%;
		margin: 0 auto;
		.nav-fixed{
			height: 100rpx;
			// background-color: #ddd;
			display: flex;
			align-items: center;
			margin-top: 20rpx;
			justify-content: space-around;
			.nav-box{
				box-sizing: border-box;
				font-size: 16px;
			}
			.nav-box-avtive{
				height: 45rpx;
				font-size: 16px;
				font-weight: 600;
				border-radius: 10rpx;
				border-bottom: 8px solid #F3D4B3;
			}
		}
	}
	.router-view{
		.introduce{
			width: 90%;
			margin: 10rpx auto;
			font-size: 14px;
			color: #333;
			line-height: 28px;
		}
		.course-box{
			display: flex;
			height: 300rpx;
			width: 96%;
			margin: 0 auto;
			justify-content: space-around;
			align-items: center;
			// background-color: #ddd;
			.c-left{
				width: 200rpx;
				border-radius: 20rpx;
				background-color: #F3D4B3;
				position: relative;
				&::after{
					content: '报名中';
					display: block;
					color: white;
					font-size: 14px;
					background-color: #FF6134;
					height: 50rpx;
					line-height: 50rpx;
					width: 100%;
					text-align: center;
					position: absolute;
					bottom:0;
					border-radius: 0 0 20rpx 20rpx;
				}
			}
			.c-right{
				// background-color: #bfc;
				width: 500rpx;
				height: 250rpx;
				overflow: hidden;
				display: flex;
				flex-direction: column;
				justify-content: space-evenly;
				.c-title{
					font-size: 16px;
					font-weight: bold;
				}
				.c-dec{
					font-size: 14px;
					overflow:hidden;
					text-overflow:ellipsis;
					white-space:nowrap;
				}
				.c-info{
					display: flex;
					justify-content: space-between;
					align-items: center;
					margin-top: 30rpx;
					font-size: 12px;
				}
			}
		}
		.li-box{
			height: 250rpx;
			display: flex;
			align-items: center;
			justify-content: space-evenly;
			// background-color: #ddd;
			.li-img-container{
				width: 230rpx;
				height: 200rpx;
				flex-shrink: 0;
				border-radius: 20rpx;
				background-color: #bfc;
			}
			.li-content{
				height: 70%;
				margin-left: 40rpx;
				display: flex;
				flex-direction: column;
				justify-content: space-evenly;
				.li-title{
					font-size: 14px;
				}
				.li-time{
					font-size: 10px;
					color: #666;
					.week{
						margin: 0 10rpx;
					}
				}
				.li-area{
					display: flex;
					justify-content: space-between;
					font-size: 12px;
					color: #666;
				}
			}
		}
	}
}
</style>
