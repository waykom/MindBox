<template>
	<view>
		<nav-list :itemList="navList"></nav-list>
		<consultant @click.native="handleGoDetail">
			呼叫
		</consultant>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				navList:[
					{id:1,name:'在线排序'},
					{id:2,name:'综合榜'},
					{id:3,name:'性价比'},
					{id:4,name:'新入驻'},
					{id:5,name:'本地'},
					{id:6,name:'咨询时长'},
					{id:7,name:'男倾听师'},
					{id:8,name:'女倾听师'}
				]
			};
		},
		methods:{
			handleGoDetail() {
				uni.navigateTo({
					url:'consultant-detail'
				})
			}
		}
	}
</script>

<style lang="less">

</style>
