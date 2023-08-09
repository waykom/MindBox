<template>
	<view class="container">
		<view class="main-img">
			w750,h420
		</view>
		<view class="main">
			<text style="height: 60rpx;font-weight: 600;">综合心理健康测评（SCL-90）</text>
			<text style="color: #FD9600;">免费体验</text>
		</view>
		<view class="count">
			<text>共30道问题（约用时15分钟）</text>
			<text>2229239人测过</text>
		</view>
		<view class="content">
			Lorem ipsum dolor sit amet consectetur adipisicing elit. Sit temporibus et, cumque recusandae, ut dolore veritatis amet repudiandae facilis mollitia possimus quis illum! Earum rem perferendis officia, expedita nisi exercitationem.
		</view>
		<view class="msg">
			<text>温馨提示：根据个人近一星期实际情况答题</text>
		</view>
		<view class="bottom-box">
			<view class="bleft">
				<text style="font-size:35px;margin-left: 40rpx;" class="iconfont">&#xe649;</text>
				<text style="font-size:40px;margin-left: 30rpx;" class="iconfont">&#xe603;</text>
			</view>
			<view class="bright">
				<button plain class="btn" @click="handleActionTest">开始测评</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		onLoad() {
			uni.setNavigationBarTitle({
				title:'在线测评'
			})
		},
		methods:{
			handleActionTest() {
				uni.navigateTo({
					url:'action-test-page'
				})
			}
		}
	}
</script>

<style lang="less">
.container{
	width: 100%;
	.main-img{
		width: 100%;
		height: 420rpx;
		background-color: #eee;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.main{
		height: 220rpx;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		// background-color: #bfc;
	}
	.count{
		width: 94%;
		margin: 0 auto;
		height: 100rpx;
		font-size: 12px;
		color: #666;
		// background-color: #bfc;
		display: flex;
		justify-content: space-between;
	}
	.content{
		width: 94%;
		margin: 0 auto;
		font-size: 14px;
		color: #444;
		line-height: 45rpx;
	}
	.msg{
		width: 94%;
		margin: 0 auto;
		height: 100rpx;
		line-height: 100rpx;
		font-size: 14px;
		color: #444;
	}
	.bottom-box{
		width: 100%;
		height: 100rpx;
		// background-color: #bfc;
		position:fixed;
		bottom: 0;
		display: flex;
		align-items: center;
		.bleft{
			flex: 3;
			height: 80rpx;
			line-height: 80rpx;
			// height: 100%;
			// background-color: #ddd;
			display: flex;
			// justify-content: space-evenly;
			color: #666;
		}
		.bright{
			flex: 4;
			height: 100%;
			.btn{
				height: 100rpx;
				line-height: 100rpx;
				border-radius: 20rpx;
				background-color: #F3D4B3;
				// width: 400rpx;
				border: none;
			}
		}
	}
}
</style>
