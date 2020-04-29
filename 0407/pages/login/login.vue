<template>
	<view >
	<input class="shurukuang" type="text" focus="true"  v-model="user" placeholder="请输入用户名" />
	<input class="shurukuang" type="text" focus="true"  v-model="pwd" placeholder="请输入密码"/>	
	<button class="denglu" @click="denglu">登录</button>
	</view>
</template>
<script>
	export default {
		data() {
			return {
				res:"",
				user:"",
				pwd:"",
				userCode:''
			}
		},
		methods: {	
			denglu:function() {
				var that=this;
				uni.request(
				{
					url:'http://192.168.1.143:8080/Users/login',
					method:'POST',
					header: {
						'content-type': 'application/x-www-form-urlencoded', 
					},				
					data:{userName:that.user,passWord:that.pwd},
					success:function(res){
						console.log(res);
						that.userCode=res.data.userCode;
						if(res.data=="yonghubucunzai"){
							uni.showModal({title:"不存在！"})
						}else{
							if(res.data=="mimacuowu"){
								uni.showModal({title:"密码错误！"})
							}
							else{
								uni.switchTab({
									url:'../index/index'
								})
								uni.setStorage({
									  key: 'storage_name',
									  data: that.user,
								})
								uni.setStorage({
									key:"storage_pwd",
									data:that.pwd,
								})
								uni.setStorage({
									key:"storage_nameCode",
									data:that.userCode,
								})
							}
						}
						}
					}
				
				)
			}
	}
	}
</script>
<style>
	.shurukuang{
		margin: 10upx;
		height: 80upx;
		width: 60%;
		/* justify-content:center; */
		align-items: center;
		border: #007AFF 2rpx solid;
		
		margin: 20upx;
		border-radius: 10upx;
		margin-left: 150upx;
	}
	.denglu{
		width: 60%;
	}
</style>
