<template>
	<view class="container">
		<view class="detail-box">
			<view class="info">
				<view class="user">
					
				</view>
				<view class="iright">
					<view class="rtop">
						<view class="title">
							<text>内向不爱说话怎么办?</text>
						</view>
						<view class="like">
							<text style="font-size: 20px;" class="iconfont">&#xef4e;</text>
						</view>
					</view>
					<view class="rbottom">
						<text>提问时间：2023.07.19 15.03</text>
					</view>
				</view>
			</view>
			<view class="content">
				<text>
					大家好，
					
					我是一个内向而不爱说话的人，最近我开始意识到这个特点对我的生活产生了一些影响。我不太善于在社交场合中与他人交流，经常觉得话题不知如何开展，也不知道该说什么。因此，我常常选择保持沉默，这让我感到有些尴尬和不自在。这种情况导致我很难结交新朋友，也感觉自己在社交活动中缺乏自信。
					
					我发现自己更愿意独处，沉浸在自己的世界中，思考和反思。虽然我很享受这种独立的感觉，但我也担心这样会让我与外界越来越疏离。我知道交流和社交对于人际关系的建立和维护非常重要，但我真的不太擅长。
					
					我很希望能够改变这种情况，更好地处理自己的内向特点，让自己在社交场合中更加自信和舒适。我想知道有没有什么方法可以帮助我主动参与社交，改善我与他人的交流，同时也尊重自己的内向需求。如果你们有类似的经历或有什么建议，希望能够分享给我。
					
					非常感谢！
				</text>
			</view>
			<view class="msg">
				<view class="a">
					<text>1020人阅读</text>
				</view>
				<view class="b">
					<text class="iconfont" style="margin-right: 8rpx;">&#xec7f;</text>
					<text>293</text>
				</view>
				<view class="c">
					<text class="iconfont" style="font-size: 18px;">&#xe603;</text>
				</view>
				<view class="d">
					<text class="iconfont" style="font-size: 16px;">&#xe649;</text>
				</view>
			</view>
		</view>
	
		<view class="answer">
			<view class="fixed">
				<text>老师解答</text>
			</view>
			<view class="answer-box" v-for="i in 3" :key="i">
				<view class="user">
					<view class="profile">
						<!-- 80rpx -->
					</view>
					<view class="info">
						<text class="name">丽丽{{i}}</text>
						<text class="time">{{ new Date().toLocaleString() }}</text>
					</view>
				</view>
				<view class="content">
					<view class="box">
						<text class="text">
							内向和不善言谈并不是问题，它是一种性格特质。许多人都是内向的，这意味着他们更喜欢独处，思考自己的感受，并在社交场合中保持相对沉默。↖(^ω^)↗如果你觉得内向性格导致了严重的情绪问题或社交障碍，不妨考虑寻求专业心理帮助。心理治疗可以帮助你更好地理解自己的内向特质，并提供有效的方法来应对挑战。最重要的是，不要因为内向而觉得自卑或局限，每个人都有不同的特点，内向也是一种独特的魅力。
						</text>
						<view class="btn-fixed">
							<text class="a ftext">回复</text>
							<text @click="openPopup" class="b ftext">打赏</text>
						</view>
					</view>
				</view>
			</view>
		</view>
		
		<uni-popup 
			ref="popup" 
			:is-mask-click="false"
			type="center">
			<view class="popup">
				<view @click="closePopup" class="pexit">
					<text style="font-size: 28px;color: #aaa;" class="iconfont">&#xe62f;</text>
				</view>
				<view class="pa">
					赏
				</view>
				<view class="pb">
					<view class="ptext">
						<text>选择打赏金额：</text>
					</view>
					<view class="pcontainer">
						<view class="pbox">1元</view>
						<view class="pbox">2元</view>
						<view class="pbox">3元</view>
						<view class="pbox">5元</view>
					</view>
				</view>
				<view class="pc">
					<text>其他金额：</text>
					<input class="pcinput" type="text" placeholder="输入金额" />
				</view>
				<view class="pd">
					<view class="dtext">
						<text>您的打赏，就是对我们的最大支持，谢谢!</text>
					</view>
					<view class="getmi">
						<text>打赏</text>
					</view>
				</view>
			</view>
		</uni-popup>
	
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		methods:{
			// 打开打赏弹窗
			openPopup() {
				this.$refs.popup.open('center')
			},
			// 关闭打赏弹窗
			closePopup() {
				this.$refs.popup.close()
			}
		},
	}
</script>

<style lang="less" scoped>
.container{
	width: 100%;
	.detail-box{
		width: 94%;
		margin: 0 auto;
		.info{
			height: 250rpx;
			// background-color: #eee;
			display: flex;
			align-items: center;
			.user{
				width: 100rpx;
				height: 100rpx;
				background-color: #ddd;
				border-radius: 50%;
			}
			.iright{
				flex:1;
				.rtop{
					display: flex;
					height: 100%;
					width: 100%;
					justify-content: space-between;
					align-items: center;
					margin-left: 20rpx;
					.title{
						font-size: 18px;
					}
					.like{
						display: flex;
						justify-content: center;
						align-items: center;
						width: 80rpx;
						color: #6160F6;
					}
				}
				.rbottom{
					font-size: 10px;
					display: flex;
					color: #666;
					justify-content: flex-end;
				}
			}
		}
		.content{
			font-size: 14px;
			line-height: 45rpx;
			color: #333;
		}
		.msg{
			// background-color: #ddd;
			height: 180rpx;
			display: flex;
			justify-content: space-evenly;
			align-items: center;
			font-size: 12px;
			color: #666;
			.a{
				margin-left: 200rpx;
			}
			.icon-active{
				color: orange;
			}
		}
	}

	.answer{
		.fixed{
			height: 120rpx;
			line-height: 160rpx;
			border-bottom: 1px solid #ddd;
			padding-left: 25rpx;
			font-weight: 600;
		}
		.answer-box{
			width: 92%;
			margin: 0 auto;
			.user{
				height: 120rpx;
				display: flex;
				align-items: center;
				.profile{
					width: 80rpx;
					height: 80rpx;
					border-radius: 50%;
					background-color: #bfc;
				}
				.info{
					display: flex;
					flex-direction: column;
					justify-content: center;
					margin-left: 15rpx;
					// background-color: #6160F6;
					.name{
						font-size: 14px;
						font-weight: 600;
					}
					.time{
						font-size: 10px;
						color: #666;
					}
				}
			}
			.content{
				display: flex;
				justify-content: flex-end;
				width: 100%;
				margin-bottom: 30rpx;
				.box{
					width: 90%;
					padding: 10rpx;
					box-sizing: border-box;
					border-radius: 10rpx;
					background-color: #eee;
					.text{
						font-size: 12px;
						color: #666;
					}
					.btn-fixed{
						width: 100%;
						height: 100rpx;
						display: flex;
						justify-content: flex-end;
						align-items: flex-end;
						.ftext{
							height: 50rpx;
							width: 100rpx;
							text-align: center;
							font-size: 12px;
							color: #555;
							line-height: 50rpx;
							background-color: #FEE9BC;
							border-radius: 10rpx;
						}
						.b {
							margin-left: 2px;
						}
					}
				}
			}
		}
	}

	.popup{
		width: 550rpx;
		height: 650rpx;
		border-radius: 20rpx;
		background-color: #fff;
		display: flex;
		flex-direction: column;
		justify-content: space-evenly;
		align-items: center;
		font-size: 14px;
		position: relative;
		.pexit{
			position: absolute;
			top: 20rpx;
			right: 30rpx;
		}
		.pa{
			background-color: #ddd;
			width: 120rpx;
			height: 120rpx;
			text-align: center;
			line-height: 120rpx;
			border-radius: 50%;
			font-size: 24px;
			background-color: #FEE9BC;
			color: #fff;
		}
		.pb{
			width: 90%;
			.pcontainer{
				display: flex;
				height: 130rpx;
				justify-content: space-evenly;
				align-items: center;
				.pbox{
					width: 100rpx;
					height: 100rpx;
					text-align: center;
					line-height: 100rpx;
					border-radius: 50%;
					background-color: #FEE9BC;
				}
			}
		}
		.pc{
			width: 90%;
			display: flex;
			align-items: center;
			.pcinput{
				font-size: 14px;
				height: 30px;
				border: 1px solid #ddd;
				padding-left: 10rpx;
			}
		}
		.pd{
			.getmi{
				width: 100%;
				height: 80rpx;
				line-height: 80rpx;
				margin-top: 20rpx;
				border-radius: 40rpx;
				text-align: center;
				background-color: #FEE9BC;
				font-size: 18px;
				// color: #666;
			}
		}
	}
}
</style>
