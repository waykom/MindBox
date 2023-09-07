<template>
	<view>
		<nav-list :itemList="navList"></nav-list>
		<view class="testList">
			<view class="box" v-for="i in 3" :key="i">
				<view class="img">
					<view class="img-container">
						
					</view>
				</view>
				<view class="content">
					<view class="title">
						<text>国际标准情商-EQ测试</text>
					</view>
					<view class="text">
						<text>
							Lorem ipsum dolor, sit amet consectetur adipisicing elit. Non, quia repellat consequatur ad neque, tenetur ab id beatae quam dicta velit error earum a asperiores explicabo incidunt suscipit, reiciendis necessitatibus.
						</text>
					</view>
					<view class="status-box">
						<view class="status">
							<text>进行中</text>
						</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				navList:[
					{id: 1, name: '全部'},
					{id: 2, name: '专业'},
					{id: 3, name: '人格'},
					{id: 4, name: '职场'},
					{id: 5, name: '人际关系'},
					{id: 6, name: '恋爱情感'},
					{id: 7, name: '趣味'},
				]
			};
		}
	}
</script>

<style lang="less" scoped>
.testList{
	width: 100%;
	.box{
		width: 94%;
		margin: 30rpx auto;
		display: flex;
		align-items: center;
		justify-content: space-between;
		.img{
			flex: 3;
			.img-container{
				width: 200rpx;
				height: 160rpx;
				background-color: #bfc;
			}
		}
		.content{
			flex: 5;
			font-size: 10px;
			.title{
				font-size: 12px;
				margin-bottom: 5rpx;
			}
			.text{
				color: #666;
				display:-webkit-box;
				// 设置可以显示的行数
				-webkit-line-clamp:3;
				-webkit-box-orient:vertical;
				overflow:hidden;
			}
			.status-box{
				display: flex;
				align-items: center;
				justify-content: flex-end;
				.status{
					border-radius: 5rpx;
					transform: translateY(20rpx);
					font-size: 8px;
					padding: 2rpx 10rpx;
					background-color: #FEE9BC;
				}
			}
		}
	}
}
</style>
