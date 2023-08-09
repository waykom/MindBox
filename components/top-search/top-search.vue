<template>
	<view class="search">
		<input class="sinput" :placeholder="placeholder">
	</view>
</template>

<script>
	export default {
		// 顶部搜索框
		name:"top-search",
		props:{
			placeholder:{
				type:String,
				default:'搜索'
			}
		},
		data() {
			return {
				
			};
		}
	}
</script>

<style lang="less">
	.search{
		display: flex;
		justify-content: center;
		margin-top: 20rpx;
		.sinput{
			width: 85%;
			box-sizing: border-box;
			height: 80rpx;
			padding-left: 28%;
			color: #333;
			border-radius: 20rpx;
			background-color: #FAFAFA;
			background-image: url('@/static/images/home/search.png');
			background-repeat: no-repeat;
			background-size: 5%;
			background-position: 25% center;
		}
	}
</style>