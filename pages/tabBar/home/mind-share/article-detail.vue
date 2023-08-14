<template>
	<view class="container">
		<view class="user">
			<view class="profile">
				<!-- 100 -->
			</view>
			<view class="info">
				<view class="name">
					<text>张三心理师</text>
				</view>
				<view class="date">
					<text>2023.07.20</text>
				</view>
			</view>
			<view class="share">
				<text class="iconfont">&#xe649;</text>
				<text class="iconfont">&#xe603;</text>
			</view>
		</view>
		<view class="head">
			<view class="img">
				<image style="width: 750rpx;" src="@/static/images/course/th.jpg" mode="widthFix"></image>
			</view>
		</view>
		<view class="article">
			<view class="fixed">
				<view class="title">
					<text>秒回消息重要吗？</text>
				</view>
				<view class="right-icon">
					<view class="read">
						<text>4565人阅读</text>
					</view>
					<view class="like">
						<text class="iconfont" style="font-size: 14px;margin-right: 5rpx;">&#xec7f;</text>
						<text>262</text>
					</view>
				</view>
			</view>
			<view class="content">
				<text>
					相处是一种艺术，需要我们用心去经营和维护。当你遇到那个值得你去爱的人时，要学会相互尊重和关注对方的感受包容对方的缺点和不足，同时也要有勇气去表达自己的需要和欲望。在相处中，要学会放下过去的不快和争执，把重点放在未来，共同创造一个充满爱和温暖的未来。每一次争执和挫折都是一次成长和学习的机会它们可以让我们更加了解对方，更加深入地理解和爱着对方。相处需要耐心和努力，但是它也是一件充满幸福和美好的事情。让我们一起用爱和关心，创造一个充满温暖和亲密的关系
				</text>
			</view>
		</view>
	
		<view class="review-container">
			<view class="text-fixed">
				<text style="font-weight: 600;">评论</text>
				<text style="font-size: 12px;color: #666;">(565)</text>
			</view>
			<view class="review-list">
				<view class="review-box">
					<view class="rtop">
						<view class="profile">
							<!--  -->
						</view>
						<view class="uinfo">
							<view class="uname">
								<text>李白</text>
							</view>
							<view class="stime">
								<text>2小时前</text>
							</view>
						</view>
						<view class="like">
							<text style="font-size: 12px;" class="iconfont">&#xec7f;</text>
							<text style="margin-left: 8rpx;">556</text>
						</view>
					</view>
					<view class="rcontent">
						<text>
							Lorem ipsum, dolor sit amet consectetur adipisicing elit. Inventore unde quo ipsa magni exercitationem vel iure dolorem architecto voluptates accusantium adipisci nihil doloremque, illum sed at natus eum iste deleniti.
						</text>
					</view>
					<view class="talk">
						<view class="talker">
							<text style="color: #179570;">gguigu:</text>
							<text>
								茶文化真的很有意思，希望有声之年可以到达大佬的境界，不说了。我去看茶文化18代了。再见朋友们!
							</text>
						</view>
						<view class="more-talker">
							<text>查看更多回复 ></text>
						</view>
					</view>
				</view>
			</view>
			<view class="showmore">
				<text>展开更多评论</text>
				<text class="iconfont" style="font-size: 10px;margin-left: 10rpx;padding-top: 5rpx;">&#xe60e;</text>
			</view>
			<view class="mytalk">
				<text>我要评论</text>
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

<style lang="less" scoped>
.container{
	width: 100%;
	.user{
		display: flex;
		height: 100rpx;
		align-items: center;
		
		width: 94%;
		margin: 0 auto;
		margin-top: 30rpx;
		.profile{
			width: 100rpx;
			height: 100rpx;
			border-radius: 50%;
			flex-shrink: 0;
			background-color: #bfc;
		}
		.info{
			font-size: 12px;
			color: #333;
			display: flex;
			flex-direction: column;
			margin: 0 auto;
			margin-left: 20rpx;
		}
		.share{
			display: flex;
			align-items: center;
			justify-content: space-evenly;
			width: 120rpx;
			flex-shrink: 0;
			// background-color: #bfc;
			color: #666;
		}
	}
	.head{
		height: 480rpx;
		// background-color: #bfc;
		display: flex;
		flex-direction: column;
		margin-top: 30rpx;
		// justify-content: space-evenly;
		align-items: center;
		.img{
			// background-color: #eee;
		}
	}
	.article{
		width: 94%;
		margin: 0 auto;
		.fixed{
			display: flex;
			align-items: center;
			justify-content: space-between;
			// background-color: #ddd;
			.title{
				font-size: 18px;
			}
			.right-icon{
				display: flex;
				align-items: center;
				font-size: 10px;
				color: #666;
				.read{
					margin-right: 15rpx;
				}
				.like{
					display: flex;
					align-items: center;
				}
			}
		}
		.content{
			margin-top: 20rpx;
			color: #555;
			font-size: 14px;
		}
	}

	.review-container{
		width: 100%;
		margin: 60rpx auto;
		.text-fixed{
			padding-left: 30rpx;
			height: 100rpx;
			line-height: 100rpx;
			// background-color: #ddd;
			border-bottom: 1px solid #ddd;
		}
		.review-list{
			width: 94%;
			margin: 30rpx auto;
			.review-box{
				margin-top: 30rpx;
				.rtop{
					height: 100rpx;
					display: flex;
					align-items: center;
					.profile{
						width: 80rpx;
						height: 80rpx;
						display: flex;
						align-items: center;
						justify-content: center;
						overflow: hidden;
						border-radius: 50%;
						background-color: #bfc;
					}
					.uinfo{
						flex: 1;
						margin-left: 20rpx;
						.uname{
							font-size: 14px;
						}
						.stime{
							font-size: 10px;
							color: #666;
						}
					}
					.like{
						display: flex;
						align-items: center;
						font-size: 10px;
						color: #666;
					}
				}
			
				.rcontent{
					font-size: 14px;
					color: #333;
					margin-left: 100rpx;
				}
				
				.talk{
					margin-top: 20rpx;
					margin-left: 100rpx;
					font-size: 10px;
					color: #666;
					background-color: #F6F6F6;
					padding: 10rpx;
					.talker{
						
					}
					.more-talker{
						margin-top: 10rpx;
						color: #179570;
					}
				}
			
			}
		}
	
		.showmore{
			height: 50rpx;
			display: flex;
			align-items: center;
			justify-content: center;
			color: #179570;
			font-size: 12px;
			border-top: 1px solid #ddd;
			// background-color: #ddd;
		}
		
		.mytalk{
			height: 100rpx;
			display: flex;
			align-items: center;
			justify-content: center;
			background-color: #FEE9BC;
		}
	
	}

}
</style>
