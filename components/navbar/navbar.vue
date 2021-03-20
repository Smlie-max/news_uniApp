<template>
	<view class="navbar">
		<view class="navbar-fixed">
			<!-- 状态栏 -->
			<view :style="{height:statusBarHeight+'px'}"></view>
			<!-- 导航栏内容 -->
			<view class="navbar-content" :style="{height:navBarHeight+'px',width:windowWidth+'px'}">
				<view class="navbar-serach">
					<view class="navbar-serach_icon">
						<image src="../../static/search-icon.png" class="search-icon"></image>
						<!-- <uni-icons type="search" size="16" color="#999"></uni-icons> -->
					</view>
					<view class="navbar-serach_text">uni-app、vue</view>
				</view>
			</view>
		</view>
		<view :style="{height:navBarHeight+statusBarHeight+'px'}"></view>
	</view>
</template>

<script>
	export default {
		name:"navbar",
		data() {
			return {
				statusBarHeight: "",	// 状态栏高度
				navBarHeight: 45,	// 导航栏高度
				windowWidth: 375
			};
		},
		created() {
			// 获取手机系统信息 
			const info = uni.getSystemInfoSync()
			// 设置状态栏的高度
			this.statusBarHeight = info.statusBarHeight
			this.windowWidth = info.windowWidth
			// h5 app mp-alipay
			// #ifndef H5 || APP-PLUS ||MP-ALIPAY
			// 获取胶囊的位置
			const menuButtonInfo = uni.getMenuButtonBoundingClientRect()

			// (胶囊底部高度 - 状态栏的高度) + (胶囊顶部高度 - 状态栏的高度) = 导航栏的高度
			this.navBarHeight = (menuButtonInfo.bottom - info.statusBarHeight) + (menuButtonInfo.top - info.statusBarHeight) + 4
			this.windowWidth = menuButtonInfo.left		
			// #endif
		}
	}
</script>

<style lang="scss">
	.navbar {
		.navbar-fixed{
			position: fixed;
			top: 0px;
			left: 0px;
			z-index: 99;
			width: 100%;
			background-color: $mk-base-color;
			.navbar-content{
				display: flex;
				justify-content: center;
				align-items: center;
				height: 45px;
				padding: 0 15px;
				box-sizing: border-box;
				.navbar-serach {
					display: flex;
					align-items: center;
					width: 100%;
					height: 30px;
					padding: 0 10px;
					background-color: #fff;
					border-radius: 30px;
					.navbar-serach_icon {
						width: 20px;
						height: 20px;
						margin-right: 6px;
						// border: 1px solid red;
						.search-icon {
							width: 100%;
							height: 100%;
							display: block;
						}
					}
					.navbar-serach_text {
						font-size: 12px;
						color: #999;
					}
				}
			}
		}
	}
</style>
