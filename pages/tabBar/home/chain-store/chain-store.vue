<template>
	<view class="container">
		<view class="typesort">
			<view class="area sortbox" @click="openLocationPopup">
				<text>全国地区</text>
				<text class="iconfont sorticon">&#xe604;</text>
			</view>
			<view class="alltype sortbox" @click="openAllTypePopup">
				<text>全部类型</text>
				<text class="iconfont sorticon">&#xe604;</text>
			</view>
		</view>
		<view class="studio-list">
			<view class="studio-box" @click="goStudioDetail">
				<view class="img-container">
					<view class="img">
						<!-- 250 200 -->
					</view>
				</view>
				<view class="info">
					<view class="name">
						<text>深圳福田区心理工作室</text>
					</view>
					<view class="worktime">
						<text>周一至周五</text>
						<text style="margin: 0 10rpx;">9:00-12:00</text>
						<text>14:00-18:00</text>
					</view>
					<view class="address">
						<text>福田区高新南一道9号中科大厦501</text>
					</view>
				</view>
			</view>
		</view>
	
		<uni-popup ref="location" type="top">
			<template>
				<view class="locations">
					<view class="nav-title">
						<text class="iconfont">&#xe675;</text>
						<text style="margin-left: 10rpx;">全部地区</text>
					</view>
					<view class="location">
						<view class="locbox" 
							v-for="name in locationList" 
							:key="name.id"
							@click="handlerLocationClick(name.id)"
							:class="locationIndex == name.id ? 'location-active' : ''"
						>
							<text>{{ name.city }}</text>
						</view>
					</view>
				</view>
			</template>
		</uni-popup>
		
		<uni-popup ref="alltype" type="top">
			<view class="type-container">
				<view class="type-title">
					<text>全部类型</text>
				</view>
				<view class="types">
					<view class="typebox" 
						v-for="name in typeList" 
						:key="name.id"
						@click="handlerTypeClick(name.id)"
						:class="typeIndex == name.id ? 'type-active' : ''"
					>
						<text>{{ name.name }}</text>
					</view>
				</view>
			</view>
		</uni-popup>
	
	</view>
</template>

<script>
	export default {
		data() {
			return {
				locationIndex: 1,
				locationList:[
					{id:1, city: '全部'},
					{id:2, city: '上海'},
					{id:3, city: '北京'},
					{id:4, city: '广州'},
					{id:5, city: '深圳'},
					{id:6, city: '成都'},
					{id:7, city: '西安'},
					{id:8, city: '哈尔滨'},
					{id:9, city: '天津'}
				],
				typeIndex: 1,
				typeList:[
					{id:1, name: '全部'},
					{id:2, name: '儿童咨询'},
					{id:3, name: '青少年咨询'},
					{id:4, name: '成人咨询'},
					{id:5, name: '总年人咨询'}
				]
			};
		},
		methods:{
			openLocationPopup() {
				this.$refs.location.open('top')
			},
			handlerLocationClick(id) {
				this.locationIndex = id
			},
			openAllTypePopup() {
				this.$refs.alltype.open('top')
			},
			handlerTypeClick(id) {
				this.typeIndex = id
			},
			goStudioDetail() {
				uni.navigateTo({
					url: 'studio-detail'
				})
			}
		}
	}
</script>

<style lang="less" scoped>
.container{
	.typesort{
		height: 80rpx;
		// background-color: #ddd;
		display: flex;
		align-items: center;
		width: 94%;
		margin: 0 auto;
		.sortbox{
			width: 150rpx;
			height: 50rpx;
			margin: 0 20rpx;
			font-size: 12px;
			color: #333;
			display: flex;
			align-items: center;
			justify-content: center;
			border-radius: 10rpx;
			background-color: #F3D4B3;
			.sorticon{
				font-size: 6px;
				padding-top: 8rpx;
				margin-left: 4rpx;
				color: #666;
			}
		}
	}
	.studio-list{
		width: 94%;
		margin: 0 auto;
		.studio-box{
			height: 250rpx;
			// background-color: #bfc;
			display: flex;
			align-items: center;
			.img-container{
				flex: 2;
				overflow: hidden;
				.img{
					width: 250rpx;
					height: 200rpx;
					border-radius: 10rpx;
					overflow: hidden;
					background-color: #ddd;
				}
			}
			.info{
				flex: 3;
				overflow: hidden;
				.name{
					font-size: 16px;
					font-weight: 600;
				}
				.worktime{
					font-size: 12px;
					margin: 10rpx 0 5rpx 0;
					color: #666;
				}
				.address{
					font-size: 12px;
					color: #666;
				}
			}
		}
	}
	
	.locations{
		box-sizing: border-box;
		padding-left: 30rpx;
		// height: calc(100vh);
		background-color: #fff;
		.nav-title{
			// font-size: 18px;
			font-weight: bold;
			padding-bottom: 30rpx;
		}
		.location{
			display: flex;
			flex-direction: column;
			.locbox{
				font-size: 14px;
				font-weight: bold;
				height: 80rpx;
				display: flex;
				align-items: center;
			}
			.location-active{
				color: #F3D4B3;
			}
		}
	}
	
	.type-container{
		box-sizing: border-box;
		padding-left: 30rpx;
		// height: calc(100vh);
		background-color: #fff;
		.type-title{
			// font-size: 18px;
			font-weight: bold;
			padding-bottom: 30rpx;
		}
		.types{
			display: flex;
			flex-direction: column;
			.typebox{
				font-size: 14px;
				font-weight: bold;
				height: 80rpx;
				display: flex;
				align-items: center;
			}
			.type-active{
				color: #F3D4B3;
			}
		}
	}
}
</style>
