<template>
	<view style="background: rgba(194,194,194,0.3); display: flex; flex-direction: column; flex: 1; height: 1306upx;">
		<view class="profile-content">
			<view class="profile-image-item" @click="camera()">
				<text style="color: #4C4C4C; font-size: 16px; flex-grow:2;">头像</text>
				<image src="../../../static/touxiang@2x.png" style="width: 60px; height: 60px; border-radius: 30px; border-color: #FFFFFF; border-width: 0.5px;"></image>
				<image class="profile-item-right-image" src="../../../static/xiaji@2x.png"></image>
			</view>
			<view class="profile-bottom-border"></view>
			<view class="profile-item" @click="changeName">
				<text style="color: #4C4C4C; font-size: 16px; flex-grow:2;">姓名</text>
				<text style="color: #4C4C4C; font-size: 16px;">{{name}}</text>
				<image class="profile-item-right-image" src="../../../static/xiaji@2x.png"></image>
			</view>
		</view>
		<view class="profile-content">
			<view class="profile-item" @click="chooseFM">
				<text style="color: #4C4C4C; font-size: 16px; flex-grow:2;">性别</text>
				<text style="color: #4C4C4C; font-size: 16px;">{{fm}}</text>
				<image class="profile-item-right-image" src="../../../static/xiaji@2x.png"></image>
			</view>
			<view class="profile-bottom-border"></view>
			<view class="profile-item" @click="changeAccount">
				<text style="color: #4C4C4C; font-size: 16px; flex-grow:2;">登录账号</text>
				<text style="color: #4C4C4C; font-size: 16px;">{{account}}</text>
				<image class="profile-item-right-image" src="../../../static/xiaji@2x.png"></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				fm: '男',
				account: 'Whde123',
				name: '吴海德'
			}
		},
		onLoad() {
			var the = this;
			uni.getStorage({
				key: 'storage_sex',
				success: function(res) {
					the.fm = res.data;
					console.log('storage_sex:' + res.data);
				}
			});

		},
		onShow() {
			var the = this;
			uni.getStorage({
				key: 'storage_name',
				success: function(res) {
					the.name = res.data;
					console.log('storage_name:' + res.data);
				}
			});
			uni.getStorage({
				key: 'storage_account',
				success: function(res) {
					the.account = res.data;
					console.log('storage_account:' + res.data);
				}
			});
		},
		methods: {
			camera() {
				uni.chooseImage({
					count: 1, //默认9
					sizeType: ['original', 'compressed'], //可以指定是原图还是压缩图，默认二者都有
					sourceType: ['album'], //从相册选择1
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
			changeName() {
				uni.navigateTo({
					url: 'change-name/change-name?name=' + this.name,
				})
			},
			changeAccount() {
				uni.navigateTo({
					url: 'change-account/change-account?account=' + this.account,
				})
			},
			chooseFM() {
				var arr = ['男', '女'];
				var the = this;
				uni.showActionSheet({
					itemList: arr,
					success: function(res) {
						the.fm = arr[res.tapIndex];
						console.log('选中了' + (arr[res.tapIndex]));
						the.saveFM();
					},
					fail: function(res) {
						console.log(res.errMsg);
					}
				});
			},
			saveFM() {
				uni.setStorage({
					key: 'storage_sex',
					data: this.fm,
					success: function() {
						console.log('storage_sex success');
					},
					fail() {
						console.log('storage_sex fail');
					}
				})
			}
		}
	}
</script>

<style>
	@import url("profile.css");
</style>
