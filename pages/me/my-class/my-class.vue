<template>
	<view class="my-class-view">
		<view class="my-class-header-view">
			<text class="my-class-header-view-title">学校信息</text>
			<view class="my-class-view-item">
				<text class="my-class-view-item-title">地区</text>
				<text class="my-class-view-item-detail">广东省深圳市南山区</text>
			</view>
			<view class="my-class-view-item-line"></view>
			<view class="my-class-view-item">
				<text class="my-class-view-item-title">学校</text>
				<text class="my-class-view-item-detail">外国语学校</text>
			</view>
			<text class="my-class-header-view-title">班级信息</text>
			<view class="my-class-view-item">
				<text class="my-class-view-item-title">班级</text>
				<text class="my-class-view-item-detail">初二 9班</text>
			</view>
			<view class="my-class-view-item-line"></view>
			<view class="my-class-view-item">
				<text class="my-class-view-item-title">老师</text>
				<text class="my-class-view-item-detail">李春江</text>
			</view>
			<view class="my-class-change-class-title" @click="changeClass">换班重新绑定</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			changeClass() {
				uni.showToast({
					title: '已经切换班级'
				});
			}
		}
	}
</script>

<style>
	.my-class-view {
		background: rgba(194, 194, 194, 0.3);
		display: flex;
		flex-direction: column;
		flex: 1;
		height: 1306upx;
	}

	.my-class-header-view {
		height: 90upx;
	}

	.my-class-header-view-title {
		font-size: 18px;
		font-family: PingFang-SC-Regular;
		font-weight: 400;
		color: rgba(156, 156, 156, 1);
		line-height: 50px;
		margin-top: 29upx;
		margin-left: 70upx;
	}

	.my-class-view-item {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		height: 125upx;
		align-items: center;
		background-color: #FFFFFF;
	}

	.my-class-view-item-title {
		font-size: 16px;
		font-family: PingFang-SC-Regular;
		font-weight: 400;
		color: rgba(76, 76, 76, 1);
		line-height: 45upx;
		margin-left: 70upx;
	}

	.my-class-view-item-detail {
		font-size: 16px;
		font-family: PingFang-SC-Regular;
		font-weight: 400;
		color: rgba(76, 76, 76, 1);
		line-height: 45px;
		margin-right: 30upx;
	}

	.my-class-view-item-line {
		margin: 0px 0upx 0upx 50upx;
		border-bottom-color: #979797;
		border-bottom-style: solid;
		border-bottom-width: 0.5px;
		margin-top: -0.5;
	}

	.my-class-change-class-title {
		height: 47px;
		font-size: 16px;
		font-family: PingFang-SC-Medium;
		font-weight: 500;
		color: rgba(254, 91, 44, 1);
		line-height: 45px;
		text-align: right;
		margin-right: 30upx;
		margin-top: 30upx;
		width: 750upx;
	}
</style>
