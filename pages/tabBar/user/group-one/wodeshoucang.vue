<template>
	<view>
		<nav-list :itemList="navList"></nav-list>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				navList: [
					{id: 1, name: '课程'},
					{id: 2, name: '趣味沙龙'},
					{id: 3, name: '文章'},
					{id: 4, name: '视频'},
				]
			}
		}
	}
</script>

<style lang="less">

</style>
