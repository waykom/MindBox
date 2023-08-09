<template>
	<view>
		<nav-list :itemList="navList"></nav-list>
		<consultant @click.native="handleDetail" v-for="(i,index) in 3" :key="index"></consultant>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				navList:[
					{id:1,name:'在线排序'},
					{id:2,name:'综合实力'},
					{id:3,name:'性价比'},
					{id:4,name:'个案数'},
					{id:5,name:'本地专家'},
					{id:6,name:'续单率'},
					{id:7,name:'新入驻'}
				]
			};
		},
		methods:{
			handleDetail() {
				uni.navigateTo({
					url:'consultant-detail'
				})
			}
		}
	}
</script>

<style lang="less">

</style>
