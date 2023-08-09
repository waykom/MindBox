<template>
	<view class="filter-container">

		<nav-list :itemList="areaList"></nav-list>
		
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
				<view v-if="filterIndex==0">
					<!-- 困惑模块 -->
					<filter-item :filterItemList="typeFilterList.queList"></filter-item>
				</view>
				<!-- 这是时间 -->
				<view v-if="filterIndex==1">
					<filter-item :filterItemList="typeFilterList.timeList">
						<template #dateSlot>
							<inline-calendar
								@change="handleDateChange"
								/>
						</template>
					</filter-item>
				</view>
				<view v-if="filterIndex==2">
					<!-- 这是价格 -->
					<filter-item :filterItemList="typeFilterList.priceList"></filter-item>
				</view>
				<view v-if="filterIndex==3">
					<!-- 这是筛选 -->
					<filter-item :filterItemList="typeFilterList.filterList"></filter-item>
				</view>
				<view v-if="filterIndex==4">
					<!-- 这是排序 -->
					<filter-item :filterItemList="typeFilterList.sortList"></filter-item>
				</view>
			</uni-popup>
		</view>
		<consultant v-for="(i,index) in 2" :key="index"></consultant>
		
		
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
					{id:4,name:'北京'},
					{id:5,name:'上海'},
					{id:6,name:'武汉'},
					{id:7,name:'哈尔滨'},
					{id:8,name:'重庆'},
					{id:9,name:'大理'}
				],
				filterList:[
					{id:1,name:'问题'},
					{id:2,name:'时间'},
					{id:3,name:'价格'},
					{id:4,name:'筛选'},
					{id:5,name:'排序'}
				],
				filterIndex:-1,
				
				typeFilterList:{
					queList:[
						{
							id:1,
							title:'情绪管理',
							items:[
								{ id:1, name:'全部', isActive:false},
								{ id:2, name:'情绪失控', isActive:false},
								{ id:3, name:'性格不合', isActive:false},
								{ id:4, name:'孤独', isActive:false},
								{ id:5, name:'情绪不稳定', isActive:false},
								{ id:6, name:'焦虑', isActive:false},
								{ id:7, name:'抑郁', isActive:false},
							]
						}
					],
					timeList:[
						{
							id:1,
							title:'预约时间段',
							items:[
								{ id:1, name:'全部', isActive:false},
								{ id:2, name:'上午', isActive:false},
								{ id:3, name:'下午', isActive:false},
								{ id:4, name:'晚上', isActive:false}
							]
						}
					],
					priceList:[
						{
							id:1,
							title:'价格区间(元)',
							items:[
								{ id:1, name:'不限', isActive:false},
								{ id:2, name:'200以下', isActive:false},
								{ id:3, name:'500以下', isActive:false},
								{ id:4, name:'500-800元', isActive:false},
								{ id:5, name:'800-1000元', isActive:false},
								{ id:6, name:'1000以上', isActive:false}
							]
						}
					],
					filterList:[
						{
							id:1,
							title:'咨询方式',
							items:[
								{ id:1, name:'全部', isActive:false},
								{ id:2, name:'视频咨询', isActive:false},
								{ id:3, name:'面谈', isActive:false}
							]
						},
						{
							id:2,
							title:'咨询师性别',
							items:[
								{ id:1, name:'全部', isActive:false},
								{ id:2, name:'男', isActive:false},
								{ id:3, name:'女', isActive:false}
							]
						}
					],
					sortList:[
						{
							id:1,
							title:'排序方式',
							items:[
								{ id:1, name:'推荐优先', isActive:false},
								{ id:2, name:'价格升序', isActive:false},
								{ id:3, name:'价格降序', isActive:false},
								{ id:4, name:'经验优先', isActive:false},
							]
						}
					]
					
				}
			}
		},
		mounted() {
		},
		methods:{
			open(index){
				this.filterIndex = index
				this.$refs.popup.open('top')
			},
			close(){
				this.filterIndex = -1
			},
			// 处理筛选时间选择模块
			handleDateChange(date) {
				console.log(date.format('YYYY-MM-DD'));
			},
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
		.area-list-li{
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