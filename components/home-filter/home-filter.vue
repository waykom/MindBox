<template>
	<view class="filter-container">
		<ul class="area-list">
			<li v-for="(area,index) in areaList" 
				:key="area.id"
				@click="goArea(index)"
				:class="areaIndex==index ? 'li-active' : ''"
				>
					{{ area.name }}
			</li>
		</ul>
		
		<view class="type-filter">
			<view class="filter-item" 
				v-for="(item,index) in filterList"
				:key="item.id"
				@click="open(index)">
				<view class="text">
					<text>{{item.name}}</text>
				</view>
				<view class="icon">
					<text 
						class="iconfont icon"
						:class="filterIndex==index ? 'filter-active' : ''"
						>&#xe604;</text>
				</view>
			</view>
			<uni-popup
					ref="popup" 
					background-color="#fff" 
					@maskClick="close"
					type="top">
				<view v-show="filterIndex==0">
					<!-- 困惑模块 -->
					<filter-item></filter-item>
				</view>
				<!-- 这是时间 -->
				<view v-show="filterIndex==1">
					
				</view>
				<view v-show="filterIndex==2">
					<!-- 这是价格 -->
					<filter-item></filter-item>
				</view>
				<view v-show="filterIndex==3">
					<!-- 这是筛选 -->
					<filter-item></filter-item>
				</view>
				<view v-show="filterIndex==4">
					<!-- 这是排序 -->
					<filter-item></filter-item>
				</view>
			</uni-popup>
		</view>
		<consultant v-for="(i,index) in 10" :key="index"></consultant>
		
		<!-- 这是时间 -->
		<template>
			<view v-show="filterIndex==1">
				<uni-datetime-picker
					@change="changeDate"
					ref="date"
					@maskClick="close"
					:clear-icon="false"
					v-model="datetimesingle"
				 />
			</view>
		</template>
		
	</view>
</template>

<script>
	export default {
		name:"home-filter",
		data() {
			return {
				areaList:[
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
				areaIndex:0,
				filterList:[
					{id:1,name:'疑惑'},
					{id:2,name:'时间'},
					{id:3,name:'价格'},
					{id:4,name:'筛选'},
					{id:5,name:'排序'}
				],
				filterIndex:-1,
				datetimesingle:''
			}
		},
		mounted() {
			this.datetimesingle = Date.now() - 2*24*3600*1000
		},
		methods:{
			goArea(index){
				this.areaIndex = index
			},
			open(index){
				this.filterIndex = index
				if (index === 1) {
					// 如果点击的是 `时间`
					// this.$refs.date.$el.style.display = 'block'
					this.$refs.date.show()
					// console.log(this.$refs.date.$el.style.display = 'block')
				} else {
					// 通过组件定义的ref调用uni-popup方法 ,如果传入参数 ，type 属性将失效 ，仅支持 ['top','left','bottom','right','center']
					this.$refs.popup.open('top')
				}
			},
			close(){
				this.filterIndex = -1
			},
			changeDate(e) {
				this.filterIndex = -1
				// 时间选择器输出的时间
				console.log('时间选择器输出的时间',e)
			}
		}
	}
</script>

<style lang="less" scoped>
.filter-container{
	.area-list{
		padding: 0;
		margin: 0;
		list-style: none;
		height: 100rpx;
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
		li{
			flex-shrink: 0;
			// width: 120rpx;
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
	.type-filter{
		display: flex;
		width: 90%;
		margin: 0 auto;
		.filter-item{
			display: flex;
			width: 100rpx;
			// background-color: #333;
			margin-right: 20rpx;
			justify-content: space-evenly;
			align-items: center;
			.text{
				font-size: 14px;
				color: #333;
			}
			.icon{
				display: inline-block;
				color: #bbb;
				font-size: 6px;
				transition: all 150ms linear;
				.filter-active{
					transform: rotate(-180deg);
				}
			}
		}
	}
	
}
</style>