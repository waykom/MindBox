<template>
	<view>
		<nav-list :itemList="orderList"></nav-list>
		<view class="none">
			<view>
				<image style="w=" src="@/static/images/user/order-none.png" mode="aspectFit"></image>
			</view>
			<view class="none-text">
				<text>亲，您还没有相关的订单哟~</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				orderList:[
					{id:0,name:'全部'},
					{id:1,name:'待支付'},
					{id:2,name:'待咨询'},
					{id:3,name:'待结算'},
					{id:4,name:'已完成'},
					{id:5,name:'已取消'},
				]
			};
		},
		onLoad({orderId}) {
			console.log(orderId)
		}
	}
</script>

<style lang="less">
.none{
	margin-top: 50rpx;
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	.none-text{
		font-size: 12px;
		color: #666;
	}
}
</style>
