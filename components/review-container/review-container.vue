<template>
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
</template>

<script>
	export default {
		name:"review-container",
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="less">
.review-container{
	width: 100%;
	margin: 20rpx auto;
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
</style>