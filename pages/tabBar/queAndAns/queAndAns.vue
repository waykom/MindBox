<template>
	<view class="container">
		<top-search placeholder="搜索你疑惑的问题"></top-search>
		<view class="hot-topic">
			<view class="title">
				<text>热门话题</text>
			</view>
			<view class="items-list">
				<view class="item-box" v-for="(i,index) in 3" :key="index">
					<view class="img">
						<image style="width: 200rpx;height: 400rpx;" src="../../../static/images/home/ic_02.png" mode="aspectFit"></image>
					</view>
					<view class="content">
						<view class="content-title">
							<text>高频常见问题</text>
						</view>
						<view class="des">
							<text class="des-text">
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
		
		<nav-list :itemList="navList"></nav-list>
		
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
					<button class="rbtn" plain>+ 关注</button>
				</view>
			</view>
			<view class="content" @click="handleDetail">
				<text class="ctext">
					我是一个内向而不爱说话的人，最近我开始意识到这个特点对我的生活产生了一些影响。我不太善于在社交场合中与他人交流，经常觉得话题不知如何开展，也不知道该说什么。因此，我常常选择保持沉默，这让我感到有些尴尬和不自在。这种情况导致我很难结交新朋友，也感觉自己在社交活动中缺乏自信。
					
					我发现自己更愿意独处，沉浸在自己的世界中，思考和反思。虽然我很享受这种独立的感觉，但我也担心这样会让我与外界越来越疏离。我知道交流和社交对于人际关系的建立和维护非常重要，但我真的不太擅长。
					
					我很希望能够改变这种情况，更好地处理自己的内向特点，让自己在社交场合中更加自信和舒适。我想知道有没有什么方法可以帮助我主动参与社交，改善我与他人的交流，同时也尊重自己的内向需求。如果你们有类似的经历或有什么建议，希望能够分享给我。
					
					非常感谢！
				</text>
			</view>
			<view class="operation">
				<view class="opitem">
					<text class="iconfont icon">&#xe623;</text>
					<text class="otext">分享</text>
				</view>
				<view class="opitem">
					<text class="iconfont icon">&#xe636;</text>
					<text class="otext">666</text>
				</view>
				<view class="opitem">
					<text class="iconfont icon">&#xec7f;</text>
					<text class="otext">666</text>
				</view>
			</view>
		</view>
		
		<view class="commit-fix" @click="handleCommit">
			<text>提问</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				navList:[
					{id:1,name:'推荐'},
					{id:2,name:'社会交际'},
					{id:3,name:'个人成长'},
					{id:4,name:'恋爱情感'},
					{id:5,name:'婚姻家庭'},
					{id:6,name:'婚姻家庭'},
					{id:7,name:'婚姻家庭'},
					{id:8,name:'恋爱情感'},
					{id:9,name:'婚姻家庭'}
				]
			};
		},
		methods:{
			handleDetail() {
				uni.navigateTo({
					url:'ans-detail-page'
				})
			},
			handleCommit() {
				uni.navigateTo({
					url:'ans-commit-page'
				})
			}
		}
	}
</script>

<style lang="less" scoped>
.container{
	width: 100%;
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
				// align-items: center;
				width: 600rpx;
				height: 400rpx;
				border-radius: 15rpx;
				border: 2px solid #F3D4B3;
				.img{
					width: 200rpx;
					height: 100%;
					border-radius: 10rpx;
					overflow: hidden;
					display: flex;
					justify-content: center;
					align-items: center;
					background-color: #eee;
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
						.des-text{
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
				.rbtn{
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
			font-size: 14px;
			color: #666;
			.ctext{
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
			.opitem{
				display: flex;
				align-items: center;
				.icon{
					margin-right: 10rpx;
					font-size: 16px;
				}
				.otext {
					font-size: 10px;
					color: #666;
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