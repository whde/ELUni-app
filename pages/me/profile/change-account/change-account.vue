<template>
	<view class="change-account-view">
		<view class="change-account-inputView">
			<input class="change-account-intput" maxlength="20" type="text" :value='account' @input="inputAccount" />
			<text class="change-account-intput-num">{{length}}/20</text>
		</view>
		<text class="change-account-msg-text">6-20个字符，由字母加数字组成，区分大小写 </text>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				account: '',
				length: 0
			}
		},
		onLoad(options) {
			this.account = options.account;
			this.length = this.account.length;
			console.log(options.account);
			console.log('change-account onLoad');
		},
		onHide() {
			this.save();
			console.log('change-account onHide');
		},
		onUnload() {
			this.save();
			console.log('change-account onUnload');
		},
		methods: {
			inputAccount: function(event) {
				if (event.target.value.length <= 20) {
					this.account = event.target.value
					this.length = this.account.length;
					console.log(this.account);
				}
			},
			save() {
				if (this.account.length > 0) {
					uni.setStorage({
						key: 'storage_account',
						data: this.account,
						success: function() {
							console.log('storage_account success');
						},
						fail() {
							console.log('storage_account fail');
						}
					});
				}
			}
		}
	}
</script>

<style>
	.change-account-view {
		background: rgba(194, 194, 194, 0.3);
		display: flex;
		flex-direction: column;
		flex: 1;
		height: 1306upx;
	}

	.change-account-inputView {
		margin-top: 26px;
		height: 50px;
		border: 0.5px solid rgba(194, 194, 194, 1);
		background: rgba(250, 250, 250, 1);
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
	}

	.change-account-intput {
		font-size: 16px;
		color: rgba(76, 76, 76, 1);
		margin-left: 25upx;
		font-family: PingFang-SC-Regular;
		font-weight: 400;
		width: 650upx;
	}

	.change-account-intput-num {
		margin-right: 25upx;
		height: 35px;
		font-size: 15;
		font-family: PingFang-SC-Regular;
		font-weight: 400;
		color: rgba(156, 156, 156, 1);
		line-height: 42px;
	}

	.change-account-msg-text {
		height: 35px;
		font-size: 15px;
		font-family: PingFang-SC-Regular;
		font-weight: 400;
		color: rgba(156, 156, 156, 1);
		line-height: 42px;
		margin-left: 27upx;
	}
</style>
