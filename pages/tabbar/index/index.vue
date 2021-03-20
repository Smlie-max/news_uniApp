<template>
	<view class="content">
		<!-- 自定义导航栏 -->
		<navbar></navbar>
		<tab :list="tabList"></tab>
	</view>
</template>

<script>
	// easyCom components/组件名/组件名.vue 局部引入,不需要像下面那样引入
	// import navbar from '../../../components/navbar/navbar.vue'
	export default {
		// components:{
		// 	navbar
		// },
		data() {
			return {
				title: 'Hello',
				tabList: []
			}
		},
		onLoad() {
			this.getLabel()
		},
		methods: {
			getLabel() {
				// 调用云函数方法
				uniCloud.callFunction({
					name: 'get_label',
				}).then((res) => {
					const {result} = res
					this.tabList = result.data
					console.log(this.tabList)
				})
			}
		}
	}
</script>

<style>
	/* .content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	} */
</style>
