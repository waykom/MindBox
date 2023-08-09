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
		
		<view class="info">
			<view class="inhead">
				<view class="title custom-underline">
					<text>报名信息</text>
				</view>
				<view class="infright">
					<text>3249人参与</text>
				</view>
			</view>
			<view class="content">
				<text class="leader">带领人：张三</text>
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
				<text>沙龙介绍</text>
			</view>
			<view class="content">
				<text class="text">
					相处是一种艺术，需要我们用心去经营和维护。当你遇到那个值得你去爱的人时，要学会相互尊重和关注对方的感受包容对方的缺点和不足，同时也要有勇气去表达自己的需要和欲望。在相处中，要学会放下过去的不快和争执，把重点放在未来，共同创造一个充满爱和温暖的未来。每一次争执和挫折都是一次成长和学习的机会，它们可以让我们更加了解对方，更加深入地理解和爱着对方。相处需要耐心和努力，但是它也是一件充满幸福和美好的事情。让我们一起用爱和关心，创造一个充满温暖和亲密的关系。
				</text>
			</view>
		</view>
		
		<view class="step">
			<view class="step-title custom-underline">
				<text>沙龙流程</text>
			</view>
			<view class="step-content">
				<text class="stcen">
					一、老师自我介绍及介绍课程规则
				</text>
				<text class="stcen">
					二、组成员分享在孩子安全感养成方面遇到的主要困难
				</text>
				<text class="stcen">
					三、老师进行内容分享
				</text>
				<text class="stcen">
					四、小组成员讨论提出疑问，老师总结与答疑
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
		methods: {
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

	.info{
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		// background-color: #ddd;
		width: 94%;
		margin: 0 auto;
		.inhead{
			width: 100%;
			display: flex;
			justify-content: space-between;
			align-items: center;
			.title{
				margin-left: 20rpx;
			}
			.infright{
				font-size: 10px;
				color: #666;
			}
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
				margin-left: 10rpx;
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

	.step{
		display: flex;
		width: 94%;
		margin: 0 auto;
		flex-direction: column;
		align-items: flex-start;
		margin-top: 70rpx;
		.step-title{
			margin-left: 20rpx;
			margin-bottom: 20rpx;
		}
		.step-content{
			display: flex;
			flex-direction: column;
			font-size: 14px;
			.stcen{
				line-height: 30px;
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
			height: 600rpx;
			flex-direction: column;
			justify-content: flex-start;
			padding-top: 30rpx;
			align-items: center;
			// background-color: #ddd;
			.hotline{
				color: #333;
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
