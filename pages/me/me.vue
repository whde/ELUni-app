<template>
	<view class="me">
		<view class="touxiang">
			<image src="../../static/touxiang@2x.png" class="touxiang-image" @click="profile"></image>
			<view class="touxiang-name-flex">
				<view class="touxiang-name">Whde</view>
				<image src="../../static/bianji@2x.png" class="touxiang-bianji"></image>
				<view class="touxiang-xiangji" @click="camera">
					<image src="../../static/xiangji@2x.png" class="touxiang-xiangji-image"></image>
				</view>
			</view>
		</view>
		<view class="me-item" @click="clickMyClass">
			<view class="me-item-name-flex">
				<view class="me-item-name-top">我的班级</view>
				<view class="me-item-name-bottom">My Class</view>
			</view>
			<view class="me-item-detail-flex">
				<view class="me-item-detail-top">八年级2班</view>
				<view class="me-item-detail-bottom">南山外国语学校</view>
			</view>
			<image class="me-item-right-image" src="../../static/xiaji@2x.png"></image>
		</view>
		<view class="me-bottom-border"></view>
		<view class="me-item">
			<view class="me-item-name-flex">
				<view class="me-item-name-top">会员中心</view>
				<view class="me-item-name-bottom">Member Center </view>
			</view>
			<view class="me-item-detail-flex-center">
				<view class="me-item-name-top">剩余<text style="color: #FF7F50;">160</text>天</view>
			</view>
			<image class="me-item-right-image" src="../../static/xiaji@2x.png"></image>
		</view>
		<view class="me-bottom-border"></view>
		<view class="me-item" @click="settings">
			<view class="me-item-name-flex">
				<view class="me-item-name-top">设置</view>
				<view class="me-item-name-bottom">Set up </view>
			</view>
			<image class="me-item-right-image" src="../../static/xiaji@2x.png"></image>
		</view>
		<view class="me-bottom-border"></view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {
			profile() {
				uni.navigateTo({
					url: 'profile/profile'
				})
			},
			camera() {
				uni.chooseImage({
					count: 1, //默认9
					sizeType: ['original', 'compressed'], //可以指定是原图还是压缩图，默认二者都有
					sourceType: ['album'], //从相册选择
					success: (chooseImageRes) => {
						const tempFilePaths = chooseImageRes.tempFilePaths;
						uni.uploadFile({
							url: 'https://www.example.com/upload', //仅为示例，非真实的接口地址
							filePath: tempFilePaths[0],
							name: 'file',
							formData: {
								'user': 'test'
							},
							success: (uploadFileRes) => {
								console.log(uploadFileRes.data);
							}
						});
					}
				});
			},
			clickMyClass() {
				uni.navigateTo({
					url: 'my-class/my-class'
				})
			},
			settings () {
				uni.navigateTo({
					url:'settings/settings'
				})
			}
		},
		onLoad() {

		}
	}
</script>

<style>
	@import url("me.css");
</style>
