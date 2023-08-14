<template>
	<view>
		<button type="primary" @click="handlerLogin">登录</button>
		<button type="default" @click="handlerLogout">退出登录</button>
		<button type="default" @click="handlerCheckSession">检查登录状态</button>
		<button type="default" @click="getUserInfo">获取用户信息</button>
		<button type="default" @click="getToken">获取Token</button>
		<button type="default" @click="userLogin">获取服务器数据</button>
		<button type="default" @click="getCode">获取code</button>
		<textarea :value="value" placeholder="msg" :maxlength="-1" />
	</view>
</template>

<script>
	export default {
		data() {
			return {
				value: '',
				code: undefined,
				appId: 'wx6c584215ddc03a18',
				appSecret: '3b7b7393b12ebb115dfd17fd60d016ff',
				openId: undefined,
				sessionKey: undefined,
				userInfo: undefined,
			};
		},
		methods:{
			handlerLogin() {
				let that = this
				// 先获取用户信息
				uni.getUserProfile({
					desc: '获取用户信息',
					lang: 'zh_CN',
					success(res) {
						// 将用户信息存一份
						that.userInfo = res.userInfo
						
						// 获取登陆码,openid,本地存储数据
						that.getJsCode()
					},
					fail(error) {
						console.log(error)
					}
				})
			},
			handlerLogout() {
				console.log('Logout')
			},
			
			// 获取code
			getJsCode() {
				let that = this
				uni.login({
					provider: 'weixin',
					scopes: 'auth_user',
					success({ code }) {
						that.code = code
						console.log('getJsCode',code)
						that.getOpenId()
					}
				})
			},
			
			// code
			getCode() {
				let that = this
				uni.login({
					success(res) {
						that.value = JSON.stringify(res)
						console.log(res)
					}
				})
			},
			
			// 获取openId
			getOpenId() {
				let that = this
				uni.request({
					url: 'https://api.weixin.qq.com/sns/jscode2session',
					data: {
						appid: this.appId,
						secret: this.appSecret,
						js_code: this.code,
						grant_type: 'authorization_code',
					},
					success(res){
						if(res.statusCode === 200) {
							that.openId = res.data.openid
							that.sessionKey = res.data.session_key
							//	本地存储
							uni.setStorageSync('token',{
								code: that.code,
								openId: res.data.openid,
								sessionKey: res.data.session_key,
								userInfo: that.userInfo
							})
							console.log('登录成功！',that.$data)
						}
					}
				})
			},
			
			getUserInfo() {
				let that = this
				uni.getUserProfile({
					desc: '获取你的信息',
					lang: 'zh_CN',
					success(res) {
						that.value = JSON.stringify(res)
						console.log(res)
					}
				})
			},
			
			// 获取token
			getToken() {
				let token = uni.getStorageSync('token')
				this.value = JSON.stringify(token)
				console.log(token)
			},
			
			// 向服务器发送数据
			userLogin() {
				let that = this
				const {code, openId, userInfo} = uni.getStorageSync('token')
				let sendData = {
					code: code,
					userid: openId,
					nickName: userInfo.nickName,
					avatarUrl: userInfo.avatarUrl,
					gender: userInfo.gender
				}
				console.log('login',sendData)
				uni.request({
					url: 'https://www.mindboxchat.com/wkjsonout/WeiXinOpenidAndLogin',
					data: sendData,
					success(res) {
						that.value = JSON.stringify(res)
						console.log('success',res)
					},
					fail(error) {
						console.log('fail',error)
					}
				})
			},
			
			
			// 检查登录状态
			handlerCheckSession() {
				let that = this
				uni.checkSession({
					success(res) {
						that.value = JSON.stringify(res)
						console.log('success,',res)
					},
					fail(error) {
						console.log('fail,',error)
					}
				})
			}
		}
	}
</script>

<style lang="less">

</style>
