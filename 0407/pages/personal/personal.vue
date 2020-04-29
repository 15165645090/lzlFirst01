<template>
	<view >
		<navigator url="../gerenxinxi/gerenxinxi"  hover-class="">
			<button type="default" class="title" >个人信息</button>
		</navigator>
		
		<navigator url="../xuefenchaxun/xuefenchaxun"  hover-class="">
			<button type="default" class="title" >学分查询</button>
		</navigator>
		
		<navigator url="../chongzhimima/chongzhimima2"  hover-class="">
			<button type="default" class="title" >重置密码</button>
		</navigator>

		<button type="default" class="title"  @click="tuichu">退出登录</button>
		
	</view>
</template>

<script>
	var _self;
	export default{
		data(){
			return{
				
			}
		},
		methods:{
			tuichu:function(){
				uni.reLaunch({
					url:"../login/login"
				})
			}
		},
		onLoad:function(){
		}
	}
</script>

<style>
	.title{
		background:#007AFF; 
		/* color: #FFFFFF; */
		width: 98%;
		margin-top: 20upx;
		height: 100upx;
		font-size: 40upx;
		border-radius: 10upx;
		/* border: 2upx solid #EEEEEE; */
		display: flex;
		justify-content: center;
		align-items: center;
	}
</style>
