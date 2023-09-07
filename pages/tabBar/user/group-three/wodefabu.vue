<template>
	<view class="container">
		<view class="nav-list">
			<view class="left">
				<view class="list">
					<view class="item-list item-list-active">
						<text>全部</text>
					</view>
					<view class="item-list">
						<text>文章</text>
					</view>
					<view class="item-list">
						<text>视频</text>
					</view>
					<view class="item-list">
						<text>图片</text>
					</view>
				</view>
			</view>
			<view class="right">
				<text class="iconfont icon">&#xe66f;</text>
			</view>
		</view>
	
		<view class="box" v-for="i in 3" :key="i">
			<view class="up-box">
				<view class="img-container">
					<view class="img">
						
					</view>
				</view>
				<view class="content">
					<view class="title">
						<text>秒回消息重要吗？</text>
					</view>
					<view class="desc">
						<text>
							Lorem ipsum dolor sit amet consectetur adipisicing elit. Esse dolorem vel nulla tempore? Aliquam, neque sed. Earum molestiae explicabo architecto. Dolorum similique molestias temporibus consequuntur architecto dolores sint ratione neque.
						</text>
					</view>
				</view>
				<view class="time">
					<view class="a">
						<text>07-27</text>
					</view>
					<view class="b">
						<text>2023</text>
					</view>
				</view>
			</view>
			<view class="down-box">
				<view class="del btn">
					<text>删除</text>
				</view>
				<view class="change btn">
					<text>修改</text>
				</view>
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

<style lang="less">
.container {
	width: 94%;
	margin: 0 auto;
	.nav-list {
		height: 100rpx;
		// background-color: #ddd;
		display: flex;
		align-items: center;
		justify-content: space-between;
		.left{
			flex: 1;
			.list{
				display: flex;
				align-items: center;
				font-size: 14px;
				.item-list{
					margin-right: 30rpx;
				}
				.item-list-active{
					font-weight: 600;
					padding: 0 20rpx;
					border-radius: 30rpx;
					background-color: #FEE9BC;
				}
			}	
		}
		.right{
			display: flex;
			align-items: center;
			justify-content: center;
			.icon{
				color: #FEE9BC;
				font-size: 30px;
			}
		}
	}

	.box{
		width: 92%;
		margin: 30rpx auto;
		.up-box{
			display: flex;
			align-items: center;
			.img-container{
				flex: 2;
				.img{
					background-color: #bfc;
					width: 200rpx;
					height: 150rpx;
				}
			}
			.content{
				flex: 3;
				.title{
					font-size: 14px;
				}
				.desc{
					font-size: 10px;
					color: #666;
					display:-webkit-box;
					// 设置可以显示的行数
					-webkit-line-clamp:4;
					-webkit-box-orient:vertical;
					overflow:hidden;
				}
			}
			.time{
				flex: 1;
				color: #666;
				.b{
					font-size: 10px;
				}
			}
		}
		.down-box{
			display: flex;
			align-items: center;
			height: 80rpx;
			// background-color: #ddd;
			justify-content: flex-end;
			.btn{
				display: flex;
				align-items: center;
				justify-content: center;
				background-color: #FEE9BC;
				font-size: 10px;
				padding: 2rpx 20rpx;
				margin: 0 4rpx;
				color: #333;
			}
		}
	}

}
</style>
