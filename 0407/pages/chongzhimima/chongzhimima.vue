<template>
	<view class="content">
		<view class="chongzhi">
			<view class="wenzi">用户名：</view>
			<input class="shuru"  type="text" focus="true" v-model="yonghuming" disabled="true"  placeholder="请输入用户名"/>
		</view >
		<view class="chongzhi">
			<view class="wenzi">原密码：</view>
			<input class="shuru"  type="text" focus="true" v-model="mima"  disabled="true" password="true" placeholder="请输入原密码"/>
		</view >	
		<view class="chongzhi">
			<view class="wenzi">新密码：</view>
			<input class="shuru"  type="text" focus="true" v-model="a" password="true" placeholder="请输入6位数新密码"/>
		</view >
		<view class="chongzhi">
			<view class="wenzi">再次确认：</view>
			<input class="shuru"  type="text" focus="true" v-model="b" password="true" placeholder="请再次确认密码"/>
		</view >
		<view>
			<button class="wancheng" type="default"  @click="wancheng">完成</button>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				yonghuming:'',
				mima:'',
				yonghuid:'',
				a:'',
				b:''
			}	
		},
		onLoad:function(){
			var that=this;
			uni.request({
				url:"http://192.168.1.143:8080/Users/getById?id=abcd",
				method:'POST',
				header: {
					'content-type': 'application/x-www-form-urlencoded', 
				},	
				success:function(res){
					console.log(res);
					that.yonghuming=res.data.data.userName;
					that.mima=res.data.data.userPsw;
					that.yonghuid=res.data.data.userCode;
				}
			})	
		},
		methods:{
			wancheng:function(){
				// 加判断
				var _self=this;
				uni.request({
					url:"http://192.168.1.143:8080/Users/updatePassByUserCode",
					method:"POST",
					header: {
						'content-type': 'application/x-www-form-urlencoded', 
					},
					data:{userCode:_self.yonghuid,passWord:_self.a},
					success:function(res){
						console.log(res);
						uni.reLaunch({
						    url: "../login/login"
						});
					}
				})
			}
			
		}
	}
		
		
</script>
<style>
	
	.chongzhi{
		display: flex;
		
	}
	.content {
		
		
	}
	.wenzi{
		background-color: #007AFF;
		color: #FFFFFF;
		border-radius: 10upx;
		font-size: 40upx;
		margin: 20upx;
		height: 80upx;
		text-align: center;
		justify-content:center;
		width: 30%;
	}
	.shuru{
		background-color:#F0F0F0;
		border-radius: 10upx;
		margin: 20upx;
		height: 80upx;
		width: 70%;
		border: #007AFF 4upx solid;
	}
	.wancheng{
		width: 95%;
		font-size: 48upx;
	}
	
</style>