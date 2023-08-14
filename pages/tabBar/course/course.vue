<template>
  <view class="container">
		<view class="search">
			<input class="sinput" placeholder="搜索你疑惑的问题">
		</view>
		<view class="nav-list">
			<view class="list-item" 
				v-for="(item,index) in navList"
				:class="navIndex == index ? 'active' : ''"
				@click="goNav(index)"
				:key="item.id">
				<text>{{ item.name }}</text>
			</view>
		</view>
		
		<nav-list :itemList="itemList[navIndex]"></nav-list>
		
		<view class="course-box" v-for="i in 3" :key="i" @click="goDetail">
			<view class="c-left">
				<image style="width: 200rpx;height: 230rpx;" src="@/static/images/home/ic_02.png" mode="aspectFit"></image>
			</view>
			<view class="c-right">
				<view class="c-title">
					<text>
						重新定义你的认识 | 欧文亚龙团体05期
					</text>
				</view>
				<view class="c-dec">
					<text>8人小组，8月8日起，每周二晚19：00开始讲课，敬请期待！	</text>
				</view>
				<view class="c-info">
					<text style="color: #666;">
						<text class="iconfont">&#xe634;</text>
						<text>广州</text>
					</text>
					<text>
						<text style="color: red;">￥6666/人</text>
					</text>
				</view>
			</view>
		</view>
  </view>
</template>

<script>
	export default {
		data() {
			return {
				navIndex:0,
				navList:[
					{id:1,name:'热门课程'},
					{id:2,name:'企事业EAP项目'},
					{id:3,name:'咨询师培训'},
				],
				itemList: [
					[
						{id:1,name:'全国'},
						{id:2,name:'深圳'},
						{id:3,name:'广州'},
						{id:4,name:'哈尔滨'},
						{id:5,name:'内蒙古'},
						{id:6,name:'武汉'},
						{id:7,name:'成都'},
						{id:8,name:'重庆'},
						{id:9,name:'大理'}
					],
					[
						{id:1,name:'综合'},
						{id:2,name:'类别'},
						{id:3,name:'招募'},
						{id:4,name:'团建'},
						{id:5,name:'联谊'}
					],
					[
						{id:1,name:'全国'},
						{id:2,name:'深圳'},
						{id:3,name:'广州'},
						{id:4,name:'哈尔滨'},
						{id:5,name:'内蒙古'},
						{id:6,name:'武汉'},
						{id:7,name:'成都'},
						{id:8,name:'重庆'},
						{id:9,name:'大理'}
					]
				],
			};
		},
		methods:{
			goNav(index) {
				this.navIndex = index
			},
			goDetail() {
				uni.navigateTo({
					url:'/pages/tabBar/course/detial'+'?title='+'重新定义你的认识 | 欧文亚龙团体05期',
				})
			}
		}
	}
</script>

<style lang="less" scoped>
.container{
	width: 100%;
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
	.nav-list{
		display: flex;
		justify-content: space-around;
		// background-color: #ddd;
		height: 100rpx;
		align-items: center;
		margin-top: 20rpx;
		.list-item{
			box-sizing: border-box;
			// background-color: #ddd;
			font-size: 18px;
		}
		.active{
			height: 50rpx;
			border-radius: 10rpx;
			border-bottom: 10px solid #F3D4B3;
		}
	}
	.area-list{
		padding: 0;
		margin: 0;
		list-style: none;
		height: 100rpx;
		// background-color: #ddd;
		width: 95%;
		margin: 0 auto;
		// margin-top: 10rpx;
		display: flex;
		overflow: auto;
		align-items: center;
		text-align: center;
		&::-webkit-scrollbar {
			display: none;
		}
		.area-list-li{
			flex-shrink: 0;
			// width: 150rpx;
			margin: 0 20rpx;
			color: #888;
			font-size: 14px;
			transition: all 0.1s linear;
		}
		.li-active{
			font-size: 20px;
			color: #333;
		}
	}

	.course-box{
		display: flex;
		height: 300rpx;
		width: 96%;
		margin: 0 auto;
		justify-content: space-around;
		align-items: center;
		// background-color: #ddd;
		.c-left{
			width: 200rpx;
			border-radius: 20rpx;
			background-color: #F3D4B3;
			position: relative;
			&::after{
				content: '报名中';
				display: block;
				color: white;
				font-size: 14px;
				background-color: #FF6134;
				height: 50rpx;
				line-height: 50rpx;
				width: 100%;
				text-align: center;
				position: absolute;
				bottom:0;
				border-radius: 0 0 20rpx 20rpx;
			}
		}
		.c-right{
			// background-color: #bfc;
			width: 500rpx;
			height: 250rpx;
			overflow: hidden;
			display: flex;
			flex-direction: column;
			justify-content: space-evenly;
			.c-title{
				font-size: 16px;
				font-weight: bold;
			}
			.c-dec{
				font-size: 14px;
				overflow:hidden;
				text-overflow:ellipsis;
				white-space:nowrap;
			}
			.c-info{
				display: flex;
				justify-content: space-between;
				align-items: center;
				margin-top: 30rpx;
				font-size: 12px;
			}
		}
	}
}
</style>
