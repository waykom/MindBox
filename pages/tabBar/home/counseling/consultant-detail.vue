<template>
	<view class="container">
		<view class="head-img"></view>
		<view class="head-info">
			<view class="top-info">
				<view class="tprofile">
					<!-- 100 -->
					<image style="width: 80rpx;height: 80rpx;" src="@/static/images/icon/tabBar/user.png" mode="aspectFit"></image>
				</view>
				<view class="tinfo">
					<view class="ta">
						<view>
							<text class="tname">张三李</text>
						</view>
						<view class="tce" style="margin-left: 10rpx;">
							<text class="tce1 iconfont">中级认证</text>
						</view>
						<view style="margin-left: 10rpx;">
							<text class="twork">深圳南山区工作室</text>
						</view>
					</view>
					<view class="bb">
						<view style="display: flex;align-items: center;">
							<text class="iconfont">&#xe634;</text>
							<text>深圳</text>
						</view>
						<view style="margin-left: 10rpx;">
							<text>初级心理咨询师</text>
						</view>
						<view style="margin-left: 10rpx;">
							<text>从业年限7年</text>
						</view>
					</view>
				</view>
				<view class="tprice">
					<view class="tpr">
						<text style="color: red;">￥<text style="font-size: 16px;">200</text></text>
						<text style="font-size: 8px; margin-left: 5rpx;">起</text>
					</view>
					<view class="bpr">
						<text class="iconfont">&#xe611;</text>
						<text style="margin-left: 20rpx;" class="iconfont">&#xe649;</text>
					</view>
				</view>
			</view>
		
			<view class="msg">
				<text>述说你的心事，以尊重、包容陪伴你</text>
			</view>
			
			<view class="ability">
				<view class="abox">
					<view class="num">
						<text>200</text>
					</view>
					<view class="aboxtext">
						<text>个案数</text>
					</view>
				</view>
				<view class="abox">
					<view class="num">
						<text>200</text>
					</view>
					<view class="aboxtext">
						<text>个案数</text>
					</view>
				</view>
				<view class="abox">
					<view class="num">
						<text>200</text>
					</view>
					<view class="aboxtext">
						<text>个案数</text>
					</view>
				</view>
				<view class="abox">
					<view class="num">
						<text>200</text>
					</view>
					<view class="aboxtext">
						<text>个案数</text>
					</view>
				</view>
			</view>
		
			<view class="goods">
				<view class="good-box" v-for="i in 6" :key="i">
					<view :class="{'gcon-active':i==1}" class="gcon">
						<text>人际关系</text>
					</view>
				</view>
			</view>
		
		</view>
		<view class="serve-box">
			<view class="nav-fixed">
				<text>服务专项</text>
			</view>
			<view class="nav">
				<view class="nav-box" v-for="i in 3" :key="i">
					<view class="nleft">
						<view class="name">
							<text>首次心理咨询</text>
						</view>
						<view class="price">
							<text>
							<text style="color: red;">￥</text>
							<text style="color: red; font-size: 14px;">200</text>
							/60分钟
							</text>
						</view>
					</view>
					<view class="nright" @click="handleBuy">
						<text>立即购买</text>
					</view>
				</view>
			</view>
		</view>
		
		<!-- 立即购买的弹出层 -->
		<uni-popup ref="popup" type="center">
			<view class="buy-popup">
				
				<view class="topfixed">
					<view class="ttitle">
						<view class="tttlet">
							<text>选择咨询方式</text>
						</view>
					</view>
					<view class="typelist">
						<view class="typebox type-active">
							<text>面谈</text>
						</view>
						<view class="typebox">
							<text>视频咨询</text>
						</view>
						<view class="typebox">
							<text>语音</text>
						</view>
					</view>
				</view>
				
				<view class="select-time">
					<view class="ttitle">
						<view class="tttlet">
							<text>选择预约时间</text>
						</view>
					</view>
					<pretty-times @change="handleSelectTimeChange" isQuantum></pretty-times>
				</view>
				
			</view>
		</uni-popup>
	
		<view class="yuyuetime">
			<view class="topt">
				<view class="tttxt custom-underline ">
					<text>预约时间</text>
				</view>
				<view class="ttdec">
					<text>咨询时间60分钟/一次</text>
				</view>
			</view>
			<view class="time-container">
				<view class="time-select">
					<text>
						{{year}}年{{month}}月
					</text>
				</view>
				<view class="timebigbox">
					<view class="timebox" v-for="(day,index) in days" :key="index">
						<view class="day">
							<text>{{day}}</text>
						</view>
						<view class="status">
							<text>已满</text>
						</view>
					</view>
				</view>
			</view>
		</view>
	
		<view class="service">
			<view class="fixed">
				<view class="fleft">
					<text>服务评价</text>
				</view>
				<view class="fright">
					<text>更多评价 ></text>
				</view>
			</view>
			<view class="value">
				<view class="val-box val-box-active">
					<text>好评(1919)</text>
				</view>
				<view class="val-box">
					<text>中评(78)</text>
				</view>
				<view class="val-box">
					<text>差评(12)</text>
				</view>
			</view>
			<view class="value-container">
				<view class="value-box" v-for="i in 5" :key="i">
					<view class="user-info">
						<view class="user-profile">
							<!-- 80 -->
						</view>
						<view class="user-name">
							<text>欢乐肥宅水</text>
						</view>
					</view>
					<view class="value-rate">
						<view class="rate-num">
							<text class="iconfont icon-active">&#xe639;</text>
							<text class="iconfont icon-active">&#xe639;</text>
							<text class="iconfont icon-active">&#xe639;</text>
							<text class="iconfont icon-active">&#xe639;</text>
							<text class="iconfont icon-active">&#xe639;</text>
							<text style="margin-left: 20rpx; font-size: 12px;color: #FF4200;">10分</text>
						</view>
						<view class="set-time">
							<text>{{new Date().toLocaleString()}}</text>
						</view>
					</view>
					<view class="value-content">
						<text>
							Lorem ipsum dolor sit amet consectetur adipisicing elit. 
						</text>
					</view>
				</view>
			</view>
		</view>
	
	</view>
</template>

<script>
	export default {
		data() {
			let date = new Date()
			let year = date.getFullYear()
			let month = date.getMonth() +1
			return {
				year,month
			};
		},
		computed:{
			days() {
				// 获取当月的总天数
				let date = new Date();
				let month = date.getMonth()+1;
				let year = date.getYear();
				let d = new Date(year,month,0);    
				let days = d.getDate();
				return days
			}
		},
		mounted() {
			// console.log(this.days)
		},
		methods:{
			handleBuy() {
				this.$refs.popup.open('center')
			},
			handleSelectTimeChange(time) {
				console.log(time)
				uni.navigateTo({
					url:'buy-success'
				})
			}
		}
	}
</script>

<style lang="less" scoped>
.container{
	width: 100%;
	// background-color: #ddd;
	background-color: #FBFBFB;
	.head-img{
		width: 100%;
		height: 450rpx;
		background-image: url('@/static/images/home/images.jpg');
		background-repeat: no-repeat;
		background-size: 100% 100%;
		background-color: #ddd;
	}
	.head-info{
		width: 94%;
		// height: 500rpx;
		padding-bottom: 70rpx;
		background-color: #fff;
		overflow: hidden;
		margin: 0 auto;
		border-radius: 20rpx;
		transform: translateY(-50rpx);
		.top-info{
			height: 180rpx;
			display: flex;
			justify-content: space-around;
			align-items: center;
			.tprofile{
				width: 100rpx;
				height: 100rpx;
				border-radius: 50%;
				background-color: orchid;
				display: flex;
				justify-content: space-around;
				align-items: center;
			}
			.tinfo{
				display: flex;
				height: 90rpx;
				flex-direction: column;
				justify-content: space-between;
				.ta{
					display: flex;
					align-items: center;
					width: 450rpx;
					.tname{
						font-size: 18px;
						font-weight: 600;
					}
					.tce{
						background-color: coral;
						height: 24rpx;
						width: 100rpx;
						padding-left: 30rpx;
						border-radius: 20rpx;
						display: flex;
						justify-content: center;
						align-items: center;
						.tce1{
							color: wheat;
							font-size: 10px;
							position: relative;
						}
						.tce1::before{
							content: '\e658';
							font-size: 15px;
							position: absolute;
							color: white;
							bottom: 0rpx;
							left: -40rpx;
						}
					}
					.twork{
						font-size: 10px;
						color: #666;
					}
				}
				.bb{
					display: flex;
					align-items: center;
					font-size: 10px;
					color: #666;
				}
			}
			.tprice{
				height: 100rpx;
				display: flex;
				flex-direction: column;
				align-items: center;
				justify-content: space-around;
				font-size: 10px;
				.bpr{
					display: flex;
					align-items: center;
					justify-content: space-around;
				}
			}
		}
	
		.msg{
			width: 85%;
			margin: 0 auto;
			font-size: 10px;
			color: #666;
			// background-color: orchid;
		}
		
		.ability{
			height: 150rpx;
			display: flex;
			align-items: center;
			justify-content: space-around;
			.abox{
				display: flex;
				flex-direction: column;
				align-items: center;
				justify-content: center;
				width: 100%;
				// background-color: #bfc;
				border-left: 1px solid #ddd;
				.num{
					color: red;
					font-size: 14px;
				}
				.aboxtext{
					color: #666;
					font-size: 12px;
				}
			}
			.abox:first-child{
				border: none;
			}
		}
		
		.goods{
			display: flex;
			flex-wrap: wrap;
			margin-left: 40rpx;
			.good-box{
				display: flex;
				height: 60rpx;
				width: 165rpx;
				justify-content: center;
				align-items: center;
				.gcon{
					width: 90%;
					height: 50rpx;
					line-height: 50rpx;
					text-align: center;
					border-radius: 15rpx;
					background-color: #F5F5F5;
					font-size: 12px;
					color: #666;
				}
				.gcon-active{
					color: #FFDDBA;
					background-color: #333333;
				}
			}
		}
		
	}
	.serve-box{
		width: 94%;
		// height: 500rpx;
		transform: translateY(-20rpx);
		background-color: #fff;
		margin: 0 auto;
		padding-bottom: 40rpx;
		border-radius: 20rpx;	
		overflow: hidden;
		.nav-fixed{
			border-bottom: 1px solid #ddd;
			height: 90rpx;
			line-height: 90rpx;
			padding-left: 30rpx;
			font-weight: 600;
		}
		.nav{
			width: 92%;
			margin: 0 auto;
			// background-color: #ddd;
			.nav-box{
				display: flex;
				height: 120rpx;
				align-items: center;
				justify-content: space-between;
				.nleft{
					font-size: 14px;
					.price{
						font-size: 10px;
					}
				}
				.nright{
					width: 160rpx;
					height: 60rpx;
					line-height: 60rpx;
					text-align: center;
					border-radius: 10rpx;
					background-color: #F3D4B3;
					font-size: 14px;
				}
			}
		}
	}

	.buy-popup{
		width: 700rpx;
		padding: 50rpx 0;
		border-radius: 20rpx;
		background-color: #fff;
		.topfixed{
			width: 90%;
			margin: 0 auto;
			.ttitle{
				height: 100rpx;
				display: flex;
				align-items: center;
				color: #462707;
				font-weight: 600;
				.tttlet{
					padding-left: 20rpx;
					border-left: 10px solid #462707;
				}
			}
			.typelist{
				display: flex;
				align-items: center;
				justify-content: space-evenly;
				height: 100rpx;
				
				.typebox{
					height: 60rpx;
					line-height: 60rpx;
					border-radius: 10rpx;
					padding: 0 30rpx;
					color: #666;
					background-color: #E1E1E1;
				}
				.type-active{
					color: #333;
					background-color: #FEE9BC;
				}
			}
		}
		.select-time{
			width: 90%;
			margin: 0 auto;
			.ttitle{
				height: 100rpx;
				display: flex;
				align-items: center;
				color: #462707;
				font-weight: 600;
				.tttlet{
					padding-left: 20rpx;
					border-left: 10px solid #462707;
				}
			}
		}
	}

	.yuyuetime{
		width: 94%;
		height: 880rpx;
		background-color: #fff;
		margin: 0 auto;
		border-radius: 20rpx;
		.topt{
			height: 130rpx;
			display: flex;
			flex-direction: column;
			align-items: flex-start;
			justify-content: center;
			padding-top: 15rpx;
			padding-left: 30rpx;
			.tttxt{
			}
			.ttdec{
				height: 60rpx;
				line-height: 60rpx;
				font-size: 12px;
				color: #666;
			}
		}
	
		.time-container{
			.time-select{
				height: 100rpx;
				line-height: 100rpx;
				font-size: 14px;
				font-weight: 700;
				padding-left: 30rpx;
				// background-color: #bfc;
			}
			.timebigbox{
				display: flex;
				flex-wrap: wrap;
				width: 98%;
				margin: 0 auto;
				.timebox{
					width: 90rpx;
					height: 110rpx;
					border-radius: 10rpx;
					background-color: #F3F4F6;
					margin: 2px;
					display: flex;
					flex-direction: column;
					align-items: center;
					justify-content: center;
					.day{
						margin-bottom: 8rpx;
						font-weight: bold;
					}
					.status{
						width: 90%;
						text-align: center;
						border-radius: 10rpx;
						background-color: #FEFFFF;
						font-size: 10px;
					}
				}
			}
		}
	
	}

	.service{
		width: 94%;
		// height: 700rpx;
		background-color: #fff;
		margin: 0 auto;
		margin-top: 20rpx;
		border-radius: 20rpx;
		overflow: hidden;
		.fixed{
			height: 150rpx;
			// background-color: #bfc;
			display: flex;
			justify-content: space-between;
			align-items: flex-end;
			box-sizing: border-box;
			padding: 0 20rpx 40rpx 20rpx;
			border-bottom: 1px solid #ddd;
			.fleft{
				font-size: 18px;
				font-weight: 600;
			}
			.fright{
				font-size: 12px;
				color: #666;
			}
		}
	
		.value {
			display: flex;
			align-items: center;
			width: 94%;
			margin: 0 auto;
			height: 100rpx;
			color: #666;
			.val-box{
				background-color: #FFEEED;
				margin-right: 20rpx;
				padding: 0 12rpx;
			}
			.val-box-active{
				color: #333;
				background-color: #F3D4B3;
			}
		}
		
		.value-container{
			width: 100%;
			.value-box{
				padding: 0 25rpx;
				box-sizing: border-box;
				border-bottom: 1px solid #ddd;
				.user-info{
					height: 100rpx;
					display: flex;
					align-items: center;
					.user-profile{
						width: 80rpx;
						height: 80rpx;
						border-radius: 50%;
						background-color: orchid;
					}
					.user-name{
						margin-left: 20rpx;
						color: #666;
						font-size: 14px;
					}
				}
				.value-rate{
					display: flex;
					height: 80rpx;
					align-items: center;
					.rate-num{
						width: 300rpx;
						display: flex;
						align-items: center;
						.icon-active{
							color: #FF4200;
						}
					}
					.set-time{
						font-size: 10px;
						color: #555;
					}
				}
				.value-content{
					color: #666;
					font-size: 14px;
					margin-bottom: 30rpx;
				}
			}
		}
	
	}

}
</style>
