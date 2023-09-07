<template>
	<view class="container">
		<view class="example">
			<!-- 基础用法，不包含校验规则 -->
			<uni-forms ref="baseForm" :modelValue="baseFormData">
				<uni-forms-item :label-width="labelWidth" label="姓名" required>
					<uni-easyinput v-model="baseFormData.name" placeholder="请输入姓名" />
				</uni-forms-item>
				<uni-forms-item :label-width="labelWidth" label="年龄" required>
					<uni-easyinput v-model="baseFormData.age" placeholder="请输入年龄" />
				</uni-forms-item>
				<uni-forms-item :label-width="labelWidth" label="性别" required>
					<uni-data-checkbox v-model="baseFormData.sex" :localdata="sexs" />
				</uni-forms-item>
				<uni-forms-item :label-width="labelWidth" label="联系方式" required>
					<uni-easyinput v-model="baseFormData.phone" placeholder="请输入联系方式" />
				</uni-forms-item>
				<uni-forms-item :label-width="labelWidth" label="资质" required>
					<uni-file-picker limit="3"></uni-file-picker>
				</uni-forms-item>
				<uni-forms-item :label-width="labelWidth" label="入行年限" required>
					<uni-easyinput v-model="baseFormData.phone" placeholder="请输入入行年限" />
				</uni-forms-item>
				<uni-forms-item :label-width="labelWidth" label="入驻类别" required>
					<uni-data-select	v-model="value" :localdata="range" :clear="false"></uni-data-select>
				</uni-forms-item>
				<uni-forms-item :label-width="labelWidth" label="所属行业协会">
					<uni-easyinput v-model="baseFormData.phone" placeholder="请输入所属行业协会" />
				</uni-forms-item>
				<uni-forms-item :label-width="labelWidth" label="荣誉和作品">
					<uni-file-picker limit="3"></uni-file-picker>
				</uni-forms-item>
				<uni-forms-item :label-width="labelWidth" label="学历证明">
					<uni-file-picker limit="3"></uni-file-picker>
				</uni-forms-item>
				<uni-forms-item :label-width="labelWidth" label="个人简历">
					<uni-file-picker limit="1" file-mediatype="all"></uni-file-picker>
				</uni-forms-item>
				<view style="height: 50rpx;"></view>
				<button type="primary">提交</button>
			</uni-forms>
		</view>
		<view style="height: 200rpx;"></view>
	</view>
</template>


<script>
	export default {
		data() {
			return{
				labelWidth: '80px',
				
				// 基础表单数据
				baseFormData: {
					name: '',
					age: '',
					sex: 2,
					phone: ''
				},
				
				// 单选数据源
				sexs: [{
					text: '男',
					value: 0
				}, {
					text: '女',
					value: 1
				}, {
					text: '保密',
					value: 2
				}],
				value: 0,
				
				range: [
					{ value: 0, text: "请选择" },
					{ value: 1, text: "一级咨询师" },
					{ value: 2, text: "二级咨询师" },
				]
			}
		}
	}
</script>

<style lang="less">
.container{
	.example{
		width: 92%;
		margin: 50rpx auto;
	}
}
</style>