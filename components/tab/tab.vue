<template>
	<view class="tab">
		<scroll-view class="tab-scroll" scroll-x >
			<view class="tab-scroll_box">
				<view class="tab-scroll_item" v-for="(item, index) in list" :key="index">
					{{item.name}}
				</view>
			</view>
		</scroll-view>
		<view class="tab-icons">
			<image src="../../static/setting-icon.png" class="set-icon"></image>
		</view>
	</view>
</template>

<script>
	export default {
		name:"tab",
		props: {
			list: {
				type: Array,
				default() {
					return []
				}
			}
		},
		data() {
			return {
				list: []
			};
		}
	}
</script>

<style lang="scss">
	.tab {
		display: flex;
		width: 100%;
		background-color: #fff;
		border-bottom: 1px solid #f5f5f5;
		box-sizing: border-box;
		.tab-scroll{
			flex: 1;
			overflow: hidden;
			box-sizing: border-box;
			.tab-scroll_box {
				display: flex;
				align-items: center;
				flex-wrap: nowrap;
				height: 45px;
				.tab-scroll_item {
					flex-shrink: 0;
					padding: 0 10px;
					color: #333;
					font-size: 14px;
				}
			}
		}
		
		.tab-icons {
			position: relative;
			display: flex;
			align-items: center;
			justify-content: center;
			width: 45px;
			&::after {
				content: '';
				position: absolute;
				top: 12px;
				bottom: 12px;
				left: 0px;
				width: 1px;
				background-color: #ddd;
			}
			.set-icon{
				width: 20px;
				height: 20px;
				display: block;
			}
		}
	}
</style>
