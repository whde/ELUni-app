<template>
	<view class="change-name-view">
		<view class="change-name-inputView">
			<input class="change-name-intput" maxlength="20" type="text" :value='name' @input="inputName" />
			<text class="change-name-intput-num">{{length}}/20</text>
		</view>
		<!-- <text class="change-name-msg-text">6-20个字符，由字母加数字组成，区分大小写 </text> -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				name: '',
				length: 0
			}
		},
		onLoad(options) {
			this.name = options.name;
			this.length = this.name.length;
			console.log(options.name);
			console.log('change-name onLoad');
		},
		onHide() {
			this.save();
			console.log('change-name onHide');
		},
		onUnload() {
			this.save();
			console.log('change-name onUnload');
		},
		methods: {
			inputName: function(event) {
				if (event.target.value.length <= 20) {
					this.name = event.target.value
					this.length = this.name.length;
					console.log(this.name);
				}
			},
			save() {
				if (this.name.length > 0) {
					uni.setStorage({
						key: 'storage_name',
						data: this.name,
						success: function() {
							console.log('storage_name success');
						},
						fail() {
							console.log('storage_name fail');
						}
					});
				}
			}
		}
	}
</script>

<style>
	.change-name-view {
		background: rgba(194, 194, 194, 0.3);
		display: flex;
		flex-direction: column;
		flex: 1;
		height: 1306upx;
	}

	.change-name-inputView {
		margin-top: 26px;
		height: 50px;
		border: 0.5px solid rgba(194, 194, 194, 1);
		background: rgba(250, 250, 250, 1);
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
	}

	.change-name-intput {
		font-size: 16px;
		color: rgba(76, 76, 76, 1);
		margin-left: 25upx;
		font-family: PingFang-SC-Regular;
		font-weight: 400;
		width: 650upx;
	}

	.change-name-intput-num {
		margin-right: 25upx;
		height: 35px;
		font-size: 15;
		font-family: PingFang-SC-Regular;
		font-weight: 400;
		color: rgba(156, 156, 156, 1);
		line-height: 42px;
	}

	.change-name-msg-text {
		height: 35px;
		font-size: 15px;
		font-family: PingFang-SC-Regular;
		font-weight: 400;
		color: rgba(156, 156, 156, 1);
		line-height: 42px;
		margin-left: 27upx;
	}
</style>
