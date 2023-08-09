<template>
	<view class="container">
		<nav-list @change="change" :itemList="navList"></nav-list>
		
		<template v-if="currentItem.id==1">
			<view class="ic-list">
				<view class="ic-box">
					<text class="iconfont icon">&#xe69b;</text>
					<text>婚姻</text>
				</view>
				<view class="ic-box">
					<text class="iconfont icon">&#xea41;</text>
					<text>健康</text>
				</view>
				<view class="ic-box">
					<text class="iconfont icon">&#xe6aa;</text>
					<text>科普</text>
				</view>
				<view class="ic-box">
					<text class="iconfont icon">&#xfac9;</text>
					<text>亲子</text>
				</view>
				<view class="ic-box">
					<text class="iconfont icon">&#xe7cf;</text>
					<text>职场</text>
				</view>
			</view>
			<view class="article-list">
				<view class="article" v-for="i in 4" :key="i">
					<view class="up">
						<view class="left">
							<view class="title">
								<text>秒回消息重要吗？</text>
							</view>
							<view class="read">
								<text>12322人阅读</text>
							</view>
							<view class="content">
								<text>
									情侣之间的沟通应该基于双方的需求和共识。如果你认为回复消息的速度很重要，可以与伴侣坦诚地谈论这个话题，了解彼此的期望和观点，以便在沟通中达成共识。关系的健康建立在相互尊重、理解和适度的沟通基础之上，而不仅仅是回复消息的速度。
								</text>
							</view>
						</view>
						<view class="right">
							<view class="img">
								<!-- 
								width: 200rpx;
								height: 180rpx;
								 -->
							</view>
						</view>
					</view>
					<view class="down">
						<view class="author">
							<text>欢乐肥宅水</text>
						</view>
						<view class="set-time">
							<text>2023.02.03</text>
						</view>
						<view class="like">
							<text style="font-size: 12px;margin-right: 5rpx;" class="iconfont">&#xec7f;</text>
							<text>1234</text>
						</view>
					</view>
				</view>
			</view>
		</template>
		
		<template v-else-if="currentItem.id==2">
			<view class="hot-video">
				<view class="hot-video-box" v-for="i in 4" :key="i">
					<view class="hvideo">
						<view class="djfkds">
							<!-- width: 240rpx;
					height: 170rpx; -->
						</view>
					</view>
					<view class="hrigh">
						<view class="htilt">
							<text>火神山的CU护士有多可爱？</text>
						</view>
						<view class="hcent">
							<text>
								跟随镜头一看，他们真的很可爱!
							</text>
						</view>
						<view class="hnews">
							<text>央视新闻</text>
							<text style="margin-left: 20rpx;">03/23</text>
						</view>
						<view class="osjfs">
							<text class="iconfont jfsdo">&#xec7f;</text>
							<text style="margin-right: 20rpx; margin-left: 5rpx;">20w</text>
							<text class="iconfont jfsdo">&#xe636;</text>
							<text style="margin-right: 20rpx; margin-left: 5rpx;">2199</text>
							<text class="iconfont jfsdo">&#xe612;</text>
							<text style="margin-right: 20rpx; margin-left: 5rpx;">1233</text>
						</view>
					</view>
				</view>
			</view>
		</template>
		
		<template v-else>
			<view class="good-img-container">
				<view class="good-img-box" v-for="i in 3" :key="i">
					<view class="user-info">
						<view class="user-profile">
							<!-- 100 -->
						</view>
						<view class="user-msg">
							<view class="user-name">
								<view class="a">
									<text>丽丽</text>
								</view>
								<view class="b">
									<text>♀</text>
								</view>
								<view class="c">
									<text>LV1</text>
								</view>
							</view>
							<view class="send-time">
								<text>2小时前</text>
							</view>
						</view>
						<view class="follow">
							<text>关注</text>
						</view>
					</view>
					<view class="img-dec">
						<text>你知道就算大雨让整个城市颠倒，我会给你怀抱。</text>
					</view>
					<view class="img-container">
						<view class="img-box" v-for="i in 4" :key="i">
							<!-- 420 230 -->
						</view>
					</view>
					<view class="down-btn">
						<view class="nm">
							<text class="iconfont nmicon">&#xe612;</text>
							<text>10</text>
						</view>
						<view class="nm">
							<text class="iconfont nmicon">&#xe636;</text>
							<text>12</text>
						</view>
						<view class="nm">
							<text class="iconfont nmicon">&#xec7f;</text>
							<text>12</text>
						</view>
					</view>
				</view>
			</view>
		</template>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				navList:[
					{id:1,name:'经典文章'},
					{id:2,name:'热门视频'},
					{id:3,name:'精选照片'}
				],
				currentItem:undefined
			};
		},
		beforeMount() {
			this.currentItem = this.navList[0]
		},
		methods:{
			change(item) {
				this.currentItem = item
			}
		}
	}
</script>

<style lang="less">
.container{
	width: 100%;
	
	/* 经典文章 */
	.ic-list{
		width: 94%;
		margin: 0 auto;
		display: flex;
		justify-content: flex-start;
		align-items: center;
		flex-wrap: wrap;
		padding: 3%;
		border-top: 1px solid #ddd;
		// background-color: #bfc;
		.ic-box{
			width: 25%;
			height: 120rpx;
			font-size: 10px;
			color: #444;
			flex-shrink: 0;
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: center;
			// background-color: #ddd;
			.icon{
				font-size: 30px;
				color: #26A1FF;
			}
		}
	}
	.article-list{
		width: 92%;
		margin: 0 auto;
		.article{
			height: 300rpx;
			// background-color: #ddd;
			display: flex;
			flex-direction: column;
			justify-content: space-evenly;
			.up{
				display: flex;
				align-items: center;
				.left{
					flex: 2 0;
					.title{
						
					}
					.read{
						font-size: 10px;
						color: #666;
						margin: 20rpx 0;
					}
					.content{
						display:-webkit-box;
						// 设置可以显示的行数
						-webkit-line-clamp:2;
						-webkit-box-orient:vertical;
						overflow:hidden;
						font-size: 12px;
						color: #333;
					}
				}
				.right{
					flex: 1 0;
					.img{
						width: 200rpx;
						height: 180rpx;
						margin-left: 20rpx;
						border-radius: 10rpx;
						background-color: #bfc;
					}
				}
			}
			.down{
				width: 94%;
				margin: 0 auto;
				display: flex;
				align-items: center;
				justify-content: space-between;
				font-size: 10px;
				color: #666;
			}
		}
	}

	
	/* 热门视频 */
	.hot-video{
		width: 100%;
		margin-top: 30rpx;
		.hot-video-box{
			width: 92%;
			margin: 0 auto;
			display: flex;
			height: 200rpx;
			align-items: center;
			// background-color: #ddd;
			padding: 0 2%;
			border-bottom: 1px solid #ddd;
			.hvideo{
				flex: 1 0;
				.djfkds{
					width: 240rpx;
					height: 170rpx;
					border-radius: 15rpx;
					overflow: hidden;
					background-color: #bfc;
				}
			}
			.hrigh{
				flex: 2 0;
				overflow: hidden;
				display: flex;
				flex-direction: column;
				justify-content: center;
				margin-left: 20rpx;
				height: 170rpx;
				// background-color: #ddd;
				.htilt{
				}
				.hcent{
					font-size: 12px;
					color: #333;
					margin:5rpx 0;
					overflow: hidden;
					text-overflow: ellipsis;
					white-space: nowrap;
				}
				.hnews{
					font-size: 12px;
					color: #333;
					margin: 5rpx 0;
				}
				.osjfs{
					font-size: 10px;
					color: #666;
					display: flex;
					// background-color: #ddd;
					height: 40rpx;
					align-items: center;
					.jfsdo{
						font-size: 14px;
					}
				}
			}
		}
	}

	/* 精选图片 */
	.good-img-container{
		width: 100%;
		padding-top: 30rpx;
		border-top: 1px solid #ddd;
		.good-img-box{
			width: 94%;
			margin: 0 auto;
			height: 480rpx;
			// background-color: #ddd;
			.user-info{
				display: flex;
				align-items: center;
				height: 120rpx;
				.user-profile{
					width: 100rpx;
					height: 100rpx;
					display: flex;
					align-items: center;
					justify-content: center;
					overflow: hidden;
					border-radius: 50%;
					background-color: #bfc;
				}
				.user-msg{
					margin-left: 20rpx;
					font-size: 14px;
					.user-name{
						// background-color: #26A1FF;
						height: 50rpx;
						display: flex;
						align-items: center;
						.b{
							margin: 0 10rpx;
							width: 30rpx;
							height: 30rpx;
							line-height: 30rpx;
							color: #fff;
							text-align: center;
							background-color: #FF9EBA;
							border-radius: 10rpx;
							font-size: 12px;
						}
						.c{
							width: 60rpx;
							height: 30rpx;
							line-height: 30rpx;
							color: #fff;
							text-align: center;
							background-color: #959DFB;
							border-radius: 10rpx;
							font-size: 12px;
						}
					}
					.send-time{
						font-size: 10px;
						color: #666;
					}
				}
				.follow{
					margin-left: 300rpx;
					width: 120rpx;
					display: flex;
					align-items: center;
					justify-content: center;
					color: #fff;
					font-size: 12px;
					height: 50rpx;
					border-radius: 40rpx;
					background-color: #627DFE;
				}
			}
		
			.img-dec{
				font-size: 14px;
				color: #222;
			}
			.img-container::-webkit-scrollbar{
				display: none;
			}
			.img-container{
				height: 260rpx;
				display: flex;
				overflow: auto;
				flex-wrap: nowrap;
				align-items: center;
				.img-box{
					flex-shrink: 0;
					margin-right: 10rpx;
					width: 420rpx;
					height: 230rpx;
					border-radius: 20rpx;
					background-color: #abcdfd;
				}
			}
			.down-btn{
				width: 90%;
				margin: 0 auto;
				display: flex;
				font-size: 10px;
				align-items: center;
				color: #666;
				justify-content: space-between;
				.nm{
					display: flex;
					align-items: center;
					.nmicon{
						margin-right: 10rpx;
					}
				}
			}
		
		}
	}
	
}
</style>
