<template>
	<view class="container">
		<view class="header">
			<text></text>
			<text>消息</text>
			<text class="iconfont">&#xe6cb;</text>
		</view>
		<uni-list :border="false">
			<uni-list :border="false" v-for="i in 5" :key="i">
				<!-- 右侧带角标 -->
				<uni-list-chat
					clickable
					@click="onClick"
					:avatar-circle="true"
					title="uni-app" 
					avatar="https://qiniu-web-assets.dcloud.net.cn/unidoc/zh/unicloudlogo.png" 
					note="您收到一条新的消息" 
					time="2020-02-02 20:20" 
					badge-text="12"
				></uni-list-chat>
			</uni-list>
		</uni-list>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		methods:{
			onClick(e) {
				console.log('执行click事件', e)
				uni.showToast({
					title: '点击反馈'
				});
			},
		}
	}
</script>

<style lang="less" scoped>
.container{
	// background-color: #F5E8F5;
	
	.header{
		height: 100rpx;
		width: 100%;
		display: flex;
		justify-content: space-between;
		align-items: center;
		text{
			width: 100rpx;
			text-align: center;
		}
	}
}
</style>
