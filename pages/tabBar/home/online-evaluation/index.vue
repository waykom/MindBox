<template>
	<view class="container">
		<top-search placeholder="搜索你想测的"></top-search>
		<nav-list :itemList="navList"></nav-list>
		<view class="hot-test">
			<view class="htop">
				<view class="htitle">
					<text>热门测评</text>
				</view>
				<view class="hrefresh">
					<text class="iconfont">&#xe6a9;</text>
					<text>换一批</text>
				</view>
			</view>
			<view class="hcontainer">
				<view class="hbox" @click="handleEnter" v-for="i in 4" :key="i">
					<view class="himg">
						w300,h180
					</view>
					<view class="hname">
						<text>心理综合测评</text>
					</view>
					<view class="hother">
						<text style="color: orange;">免费测评</text>
						<text>1234人测过</text>
					</view>
				</view>
			</view>
		</view>
	
		<view class="all-test">
			<view class="atop">
				<view class="htitle">
					<text>大家都在测</text>
				</view>
			</view>
			<view class="acontainer">
				<view class="abox" v-for="i in 4" :key="i">
					<view class="aimg">
						w705,h300
					</view>
					<view class="atitle">
						<text>国际标准情商——EQ测试</text>
					</view>
					<view class="acentent">
						<text>
							Lorem ipsum dolor sit amet consectetur adipisicing elit. Quam, molestiae enim totam numquam corporis distinctio aliquam quaerat repellat pariatur asperiores. Sint quibusdam dicta officia commodi amet eum velit facere similique?
						</text>
					</view>
					<view class="aother">
						<text style="color: orange;">免费测评</text>
						<text>1234人测过</text>
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
					{id:1,name:'全部'},
					{id:2,name:'专业'},
					{id:3,name:'人格'},
					{id:4,name:'职场'},
					{id:5,name:'人际关系'},
					{id:6,name:'恋爱情感'},
					{id:7,name:'趣味'}
				]
			}
		},
		methods:{
			handleEnter() {
				uni.navigateTo({
					url:'enter-test-page'
				})
			}
		}
	}
</script>

<style lang="less" scoped>
	// 小标题样式
.htitle{
	font-size: 18px;
	font-weight: 600;
	padding-left: 20rpx;
	border-left: 10px solid #F1DDF1;
}
.container{
	width: 100%;
	.hot-test{
		width: 100%;
		.htop{
			height: 120rpx;
			margin-top: 10rpx;
			border-top: 1px solid #ddd;
			// background-color: #ddd;
			display: flex;
			justify-content: space-between;
			align-items: center;
			.hrefresh{
				margin-right: 20rpx;
				font-size: 10px;
				color: #666;
				display: flex;
				align-items: center;
			}
		}
		.hcontainer::-webkit-scrollbar{
			display: none;
		}
		.hcontainer{
			width: 100%;
			display: flex;
			overflow: auto;
			.hbox{
				flex-shrink: 0;
				width: 300rpx;
				height: 300rpx;
				// background-color: #ddd;
				margin-left: 20rpx;
				display: flex;
				flex-direction: column;
				justify-content: space-evenly;
				.himg{
					width: 100%;
					height: 180rpx;
					overflow: hidden;
					display: flex;
					justify-content: center;
					align-items: center;
					border-radius: 20rpx;
					background-color: #eee;
				}
				.hname{
					font-size: 12px;
				}
				.hother{
					display: flex;
					justify-content: space-between;
					font-size: 10px;
				}
			}
		}
	}

	.all-test{
		width: 100%;
		.atop{
			height: 120rpx;
			display: flex;
			align-items: center;
		}
		.acontainer{
			width: 100%;
			.abox{
				height: 550rpx;
				// background-color: #ddd;
				display: flex;
				flex-direction: column;
				justify-content: space-evenly;
				background-color: #fff;
				padding: 0rpx 20rpx 20rpx 20rpx;
				border-bottom: 1px solid #eee;
				.aimg{
					width: 100%;
					height: 300rpx;
					display: flex;
					justify-content: center;
					align-items: center;
					background-color: #eee;
					border-radius: 20rpx;
					overflow: hidden;
				}
				.atitle{
					font-size: 16px;
					font-weight: 600;
				}
				.acentent{
					font-size: 12px;
					color: #333;
					display:-webkit-box;
					// 设置可以显示的行数
					-webkit-line-clamp:2;
					-webkit-box-orient:vertical;
					overflow:hidden;
				}
				.aother{
					display: flex;
					justify-content: space-between;
					font-size: 10px;
				}
			}
		}
	}

}
</style>
