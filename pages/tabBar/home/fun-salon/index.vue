<template>
	<view class="container">
		<view class="hot-activity">
			<view class="title">
				<view class="dog">
					<text>热门活动</text>
				</view>
			</view>
			<view class="content">
				<view class="box" @click="handleGoDetail" v-for="i in 6" :key="i">
					<view class="img">
						<!-- 227 200 -->
					</view>
					<view class="box-title">
						<text>如何让孩子更有安全感 | 父母解忧沙龙</text>
					</view>
					<view class="time">
						<text class="mon f">7月21日</text>
						<text class="week f">周五</text>
						<text class="hour f">9：00-18：00</text>
					</view>
					<view class="area-price">
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
		
		<nav-list :itemList="navList"></nav-list>
		
		<view class="type-activity">
			<view class="list">
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
		</view>
	
		<view @click="handleAddSalon" class="fixed">
			<text class="iconfont icon">&#xe709;</text>
		</view>
	
	</view>
</template>

<script>
	export default {
		data() {
			return {
				navList:[
					{id:1,name:'综合'},
					{id:2,name:'读书会'},
					{id:3,name:'冥想放松'},
					{id:4,name:'正念'},
					{id:5,name:'公益活动'}
				]
			};
		},
		methods:{
			handleGoDetail() {
				uni.navigateTo({
					url:'detail'
				})
			},
			handleAddSalon() {
				uni.navigateTo({
					url:'add-salon'
				})
			}
		}
	}
</script>

<style lang="less">
.container{
	width: 100%;
	.hot-activity{
		width: 94%;
		
		margin: 0 auto;
		.title{
			height: 150rpx;
			display: flex;
			align-items: center;
			.dog{
				font-size: 18px;
				line-height: 8px;
				font-weight: 600;
				border-bottom: 10px solid #F6E6F6;
				border-radius: 10rpx;
			}
		}
		.content{
			display: flex;
			flex-wrap: wrap;
			.box{
				width: 32%;
				height: 415rpx;
				.img{
					width: 227rpx;
					height: 200rpx;
					overflow: hidden;
					border-radius: 20rpx;
					background-color: #bfc;
				}
				.box-title{
					width: 92%;
					margin: 0 auto;
					font-size: 12px;
					display:-webkit-box;
					// 设置可以显示的行数
					-webkit-line-clamp:2;
					-webkit-box-orient:vertical;
					overflow:hidden;
					margin-top: 20rpx;
				}
				.time{
					width: 92%;
					margin: 0 auto;
					font-size: 10px;
					overflow: hidden;
					text-overflow: ellipsis;
					white-space: nowrap;
					color: #666;
					margin-top: 12rpx;
					.week{
						margin: 0 15rpx;
					}
				}
				.area-price{
					width: 92%;
					margin: 0 auto;
					display: flex;
					margin-top: 20rpx;
					font-size: 12px;
					color: #666;
					justify-content: space-between;
				}
			}
			.box:nth-child(3n-1){
				margin: 0 2%;
			}
		}
	}

	.type-activity{
		width: 100%;
		border-top: 1px solid #ddd;
		.list{
			width: 92%;
			margin: 0 auto;
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

	.fixed{
		position: fixed;
		width: 100rpx;
		height: 100rpx;
		border-radius: 50%;
		background-color: #F6E6F6;
		right: 10px;
		bottom: 50px;
		display: flex;
		justify-content: center;
		align-items: center;
		.icon{
			font-size: 60px;
			color: #fff;
		}
	}
}
</style>
