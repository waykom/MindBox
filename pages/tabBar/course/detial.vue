<template>
	<view class="container">
		<view class="head">
			<view class="img">
				<image style="width: 750rpx;" src="@/static/images/course/th.jpg" mode="widthFix"></image>
			</view>
			<view class="text">
				<text>重新定义你的人生 | 让关系流动起来</text>
			</view>
		</view>
		
		<view class="info">
			<view class="title custom-underline">
				<text>课程信息</text>
			</view>
			<view class="content">
				<text class="leader">代领人：张三</text>
				<text class="leader">费用：1118元/人</text>
				<text class="leader">时间：8月6日起，每周日19：00-20：30，共	20次</text>
				<text class="leader">地点：福田工作室</text>
				<text class="leader">名额：20人</text>
			</view>
			<view class="schedule">
				<view class="progress">
					<progress
						:stroke-width="20"
						border-radius="100"
						activeColor="#F3D4B3" 
						percent="50"  />
				</view>
				<text class="text">剩余10名额/20名额</text>
			</view>
		</view>
		
		<view class="intro">
			<view class="title custom-underline">
				<text>课程介绍</text>
			</view>
			<view class="content">
				<text class="text">
					相处是一种艺术，需要我们用心去经营和维护。当你遇到那个值得你去爱的人时，要学会相互尊重和关注对方的感受包容对方的缺点和不足，同时也要有勇气去表达自己的需要和欲望。在相处中，要学会放下过去的不快和争执，把重点放在未来，共同创造一个充满爱和温暖的未来。每一次争执和挫折都是一次成长和学习的机会，它们可以让我们更加了解对方，更加深入地理解和爱着对方。相处需要耐心和努力，但是它也是一件充满幸福和美好的事情。让我们一起用爱和关心，创造一个充满温暖和亲密的关系。
				</text>
			</view>
		</view>
		
		<view class="atten">
			<view class="title custom-underline">
				<text>注意事项</text>
			</view>
			<view class="content">
				<text class="text">
					开课前3天、如遇天气等不可抗拒原因需要改期的.老师因培训等时间冲突需延期的不予退费
				</text>
			</view>
			<view class="contact">
				<view class="hotline">
					<text>咨询电话：16161616</text>
				</view>
				<view class="qr">
					二维码
				</view>
			</view>
		</view>
		
		<view class="btn">
			<view class="price">
				<text>￥118</text>
			</view>
			<button plain class="sign-up-now">立即报名</button>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		onLoad( {title} ){
			uni.setNavigationBarTitle({
				title
			})
		},
		methods: {
		}
	}
</script>

<style lang="less" scoped>
.container{
	width: 100%;
	.head{
		height: 630rpx;
		// background-color: #bfc;
		display: flex;
		flex-direction: column;
		margin-top: 30rpx;
		// justify-content: space-evenly;
		align-items: center;
		.img{
			// background-color: #eee;
		}
		.text{
			width: 92%;
			font-size: 26px;
			font-weight: bold;
		}
	}

	.info{
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		// background-color: #ddd;
		width: 94%;
		margin: 0 auto;
		.title{
			margin-left: 20rpx;
		}
		.content{
			display: flex;
			flex-direction: column;
			margin-top: 20rpx;
			.leader{
				height: 65rpx;
				line-height: 65rpx;
				// background-color: #bfc;
			}
		}
		.schedule{
			display: flex;
			width: 100%;
			align-items: center;
			margin-top: 20rpx;
			.progress{
				width: 80%;
				height: 40rpx;
				border-radius: 20rpx;
				overflow: hidden;
				background-color: #ddd;
			}
			.text{
				font-size: 8px;
			}
		}
	}

	.intro{
		display: flex;
		width: 94%;
		flex-direction: column;
		align-items: flex-start;
		margin: 0 auto;
		margin-top: 70rpx;
		.title{
			margin-left: 20rpx;
		}
		.content{
			margin-top: 30rpx;
			.text{
				height: 55rpx;
				line-height: 55rpx;
				font-size: 14px;
			}
		}
	}

	.atten{
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		width: 94%;
		margin: 0 auto;
		margin-top: 40rpx;
		.title{
			margin-left: 20rpx;
		}
		.content{
			margin-top: 30rpx;
			.text{
				height: 55rpx;
				line-height: 55rpx;
				font-size: 14px;
			}
		}
		.contact{
			display: flex;
			width: 100%;
			height: 500rpx;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			// background-color: #ddd;
			.hotline{
				
			}
			.qr{
				margin-top: 30rpx;
				width: 250rpx;
				height: 250rpx;
				background-color: #bfc;
			}
		}
	}
	
	.btn{
		position: fixed;
		width: 100%;
		bottom: 0;
		left: 50%;
		transform: translateX(-50%);
		display: flex;
		align-items: center;
		background-color: #fff;
		.price{
			flex: 1;
			display: flex;
			align-items: center;
			justify-content: center;
			font-size: 18px;
			color: red;
		}
		.sign-up-now{
			flex: 1;
			// margin-right: 20rpx;
			height: 80rpx;
			line-height: 80rpx;
			background-color: #F6E6F6;
			border: none;
			border-radius: 20rpx;
		}
	}

}
</style>
