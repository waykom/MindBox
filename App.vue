<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	/* @import '~@/wxcomponents/vant-weapp/dist/common/index.wxss'; */

	@font-face {
		font-family: 'iconfont';
		src: url('~@/static/iconfont/iconfont.woff2') format('woff2'),
			url('~@/static/iconfont/iconfont.woff') format('woff'),
			url('~@/static/iconfont/iconfont.ttf') format('truetype');
	}

	.iconfont {
		font-family: "iconfont" !important;
		font-size: 16px;
		font-style: normal;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
	}

	// 自定义小标题下划线
	.custom-underline {
		height: 55rpx;
		/* width: 200rpx; */
		box-sizing: border-box;
		font-size: 20px;
		font-weight: 600;
		border-bottom: 25rpx solid #F3D4B3;
		border-radius: 10rpx;
	}

	/* #ifdef APP-PLUS  || H5*/
	uni-swiper .uni-swiper-dot {
		width: 60rpx;
		height: 4rpx;
		border-radius: 6rpx;
	}

	uni-swiper .uni-swiper-dot-active {
		width: 60rpx;
		border-radius: 6rpx;
	}


	/* #endif */

	/* #ifdef MP-WEIXIN */
	wx-swiper .wx-swiper-dot {
		width: 60rpx;
		height: 4rpx;
		border-radius: 6rpx;
	}

	wx-swiper .wx-swiper-dot-active {
		width: 60rpx;
		height: 4rpx;
		border-radius: 6rpx;
	}

	/* #endif */
</style>