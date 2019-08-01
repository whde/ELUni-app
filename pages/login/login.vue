<template>
	<view class="login">
		<image src="../../static/logo01@2x.png" class="logo"></image>
		<view class="login-user">
			<image src="../../static/denglu02@2x.png" class="login-item-image"></image>
			<input class="login-item-input" maxlength="20"  @input="inputName" :value='name' placeholder="请输入用户名"/>
		</view>
		<view class="login-bottom-border"></view>
		<view class="login-password">
			<image src="../../static/mima02@2x.png" class="login-item-image"></image>
			<input class="login-item-input" @input="inputPassword" :value='password' password="true" placeholder="请输入用密码"/>
		</view>
		<view class="login-bottom-border"></view>
		<view class="uni-padding-wrap uni-common-mt">
			<button 
			 :disabled="disabled"
			type="primary" 
			class="login-button" 
			plain="true"
			@click="loginClick"
			>登录</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				disabled:true,
				name:'Whde',
				password:'123'
			}
		},
		onLoad() {
			this.checkDisabled()
			this.loginClick();
		},
		methods: {
			loginClick() {
				uni.hideKeyboard()
				if (this.name == 'Whde'&&this.password==123){
					console.log('登录成功')
					uni.switchTab({
						url:'../index/index'
					})
				} else {
					uni.showToast({
						title:'账号密码错误'
					})
				}
			},
			checkDisabled() {
				if(this.name.length>0&&this.password.length>0) {
					this.disabled = false
				}
			},
			inputName : function(event){
				this.name = event.target.value
				this.checkDisabled()
			},
			inputPassword : function(event) {
				this.password = event.target.value
				this.checkDisabled()
			}
		}
	}
</script>

<style>
	@import url("login.css");
</style>
