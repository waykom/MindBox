<template>
	<view class="container">
		<view class="test-box">
			<view class="topic">
				<text>1. 我受背疼之苦</text>
			</view>
			<view class="box">
				<uni-data-checkbox
					v-model="value"
					mode="list"
					multiple
					max="1"
					:localdata="range"
					@change="change">
				</uni-data-checkbox>
			</view>
		</view>
		
		<view class="commit">
			<button @click="handleCommit" plain class="commit-btn">提交</button>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				value: 0,
				range: [
					{value: 0,text: "总是"	},
					{value: 1,text: "经常"},
					{value: 2,text: "有时"},
					{value: 3,text: "很少"},
					{value: 4,text: "从未"},
				]
			};
		},
		onLoad() {
			uni.setNavigationBarTitle({
				title:'在线测评'
			})
		},
		methods: {
			change(e){
				console.log('e:',e)
			},
			handleCommit() {
				uni.navigateTo({
					url:'test-result-page'
				})
			}
		}
	}
</script>

<style lang="less" scoped>
.container{
	width: 100%;
	.test-box{
		width: 94%;
		margin: 0 auto;
		.topic{
			height: 100rpx;
			line-height: 100rpx;
			// background-color: #ddd;
		}
		.box{
			border: 1px solid #ddd;
			border-radius: 10rpx;
			// height: 100rpx;
			padding: 0 30rpx;
		}
	}
	.commit{
		margin-top: 200rpx;
		.commit-btn{
			width: 200rpx;
			height: 80rpx;
			line-height: 80rpx;
			background-color: #ddd;
		}
	}
}
</style>