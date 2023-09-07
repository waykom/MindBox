<template>
	<view class="container">
		<view class="info-list">
			<uni-list :border="false">
				<uni-list-item :border="false" class="list-item" title="头像" link>
					<template v-slot:footer>
						<image class="slot-image" style="width: 50rpx;height: 50rpx;" src="@/static/images/icon/tabBar/user-selected.png" mode="widthFix"></image>
					</template>
				</uni-list-item>
				<uni-list-item 
					:border="false" 
					class="list-item"
					v-for="item in userInfo" :key="item.id"
					:title="item.key" 
					link>
					<template v-slot:footer>
						<text class="slot-text">{{item.value}}</text>
					</template>
				</uni-list-item>
			</uni-list>
		</view>
		<view class="options">
			<text>退出当前账号</text>
		</view>
		<view class="options">
			<text>注销当前账号</text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userInfo:[
					{id:1, key:'账号', value:'丽丽'},
					{id:2, key:'姓名', value:'大宝'},
					{id:3, key:'邮箱', value:'未填写'},
					{id:4, key:'手机', value:'未填写'},
				]
			};
		}
	}
</script>

<style lang="less" scoped>
.container{
	height: 100vh;
	background-color: #F6F6F6;
	.list-item{
		// height: 120rpx;
		.slot-text{
			font-size: 14px;
			color: #3b4144;
		}
	}
	.options{
		height: 100rpx;
		background-color: #fff;
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: 14px;
		color: #3b4144;
		margin-top: 10rpx;
	}
}
</style>
