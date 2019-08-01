<template>
	<view class="settings-view">
		<view class="settings-view-item settings-view-item-top">
			<text class="settings-view-item-title">修改密码</text>
			<image class="settings-view-item-right-image" src="../../../static/xiaji@2x.png"></image>
		</view>
		<view class="settings-view-item-line"></view>
		<view class="settings-view-item">
			<text class="settings-view-item-title">手机绑定</text>
			<text class="settings-view-item-detail">{{phone}}</text>
			<image class="settings-view-item-right-image" src="../../../static/xiaji@2x.png"></image>
		</view>
		<view class="settings-view-item settings-view-item-top">
			<text class="settings-view-item-title">开启消息通知</text>
			<switch :checked="notificationChecked" @change="switchChange" />
			<image class="settings-view-item-right-image" src="../../../static/xiaji@2x.png"></image>
		</view>
		<view class="settings-view-item-line"></view>
		<view class="settings-view-item">
			<text class="settings-view-item-title">清理缓存</text>
			<text class="settings-view-item-detail">{{cache}}</text>
			<image class="settings-view-item-right-image" src="../../../static/xiaji@2x.png"></image>
		</view>
		<view class="settings-view-item settings-view-item-top">
			<text class="settings-view-item-title">关于我们</text>
			<image class="settings-view-item-right-image" src="../../../static/xiaji@2x.png"></image>
		</view>
		<view class="settings-view-item-line"></view>
		<view class="settings-view-item">
			<text class="settings-view-item-title">帮助中心</text>
			<image class="settings-view-item-right-image" src="../../../static/xiaji@2x.png"></image>
		</view>
		<view class="settings-view-item-line"></view>
		<view class="settings-view-item">
			<text class="settings-view-item-title">意见反馈</text>
			<image class="settings-view-item-right-image" src="../../../static/xiaji@2x.png"></image>
		</view>
		<view class="settings-view-logout" @click="logout">退出登录</view>
	</view>
</template>

<script>
	// #ifdef APP-PLUS
	import permision from "../../../js_sdk/wa-permission/permission.js"
	// #endif
	export default {
		data() {
			return {
				phone: '15814045532',
				notificationChecked: true,
				cache: '9.7M'
			}
		},
		onShow() {
			if (uni.getSystemInfoSync().platform == "ios") {
				this.notificationChecked = permision.judgeIosPermission('push');
				console.log(this.notificationChecked);
			}
		},
		methods: {
			switchChange() {
				permision.gotoAppPermissionSetting();
			},
			logout() {
				uni.showActionSheet({
					itemList: ['退出登录？'],
					success: res => {
						uni.reLaunch({
							url: '../../login/login'
						})
					},
				});
			},
		}
	}
</script>

<style>
	.settings-view {
		background: rgba(194, 194, 194, 0.3);
		display: flex;
		flex-direction: column;
		flex: 1;
		height: 1306upx;
	}

	.settings-view-item {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		height: 125upx;
		align-items: center;
		background-color: #FFFFFF;
	}

	.settings-view-item-top {
		margin-top: 20upx;
	}

	.settings-view-item-title {
		font-size: 16px;
		font-family: PingFang-SC-Regular;
		font-weight: 400;
		color: rgba(76, 76, 76, 1);
		line-height: 45upx;
		margin-left: 70upx;
		flex-grow: 2;
	}

	.settings-view-item-detail {
		font-size: 16px;
		font-family: PingFang-SC-Regular;
		font-weight: 400;
		color: rgba(156, 156, 156, 1);
		line-height: 45upx;
	}

	.settings-view-item-right-image {
		width: 20upx;
		height: 25upx;
		align-self: center;
		margin-left: 8upx;
		margin-right: 38upx;
	}

	.settings-view-item-line {
		margin: 0px 0upx 0upx 50upx;
		border-bottom-color: #979797;
		border-bottom-style: solid;
		border-bottom-width: 0.5px;
		margin-top: -0.5;
	}

	.settings-view-logout {
		font-size: 17px;
		font-family: PingFang-SC-Medium;
		font-weight: 500;
		text-align: center;
		line-height: 50px;
		color: white;
		margin-top: 68upx;
		margin-left: 80upx;
		margin-right: 80upx;
		background: rgba(254, 91, 44, 1);
		height: 50px;
		border-radius: 4px;
	}
</style>
