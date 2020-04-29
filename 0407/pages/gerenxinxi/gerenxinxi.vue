<template>
	<view>
		<view class="yangshi">
			<input  class="yangshi1" value="姓名" disabled="true" />
			<input class="yangshi2" v-model="xingming" disabled="true"/>
		</view>
		<view class="yangshi">
			<input  class="yangshi1" value="性别" disabled="true" />
			<input  class="yangshi2" v-model="xingbie" disabled="true"/>
		</view>
		<view class="yangshi">
			<input  class="yangshi1" value="学校" disabled="true" />
			<input  class="yangshi2" v-model="xuexiao" disabled="true"/>
		</view>
		<view class="yangshi">
			<input  class="yangshi1" value="专业" disabled="true" />
			<input  class="yangshi2" v-model="zhuanye" disabled="true"/>
		</view>
	</view>
</template>
<script>
	export default {
		data() {
			return {
				xingming:'',
				xingbie:'',
				xuexiao:'',
				zhuanye:'',	
			}
		},
		onLoad:function(){
			var _self=this;
			uni.request({
				url:"http://192.168.1.143:8080/Users/getById?id=abcd",
				method:"POST",
				header: {'content-type': 'application/x-www-form-urlencoded', },
				success:function(res){
					console.log(res);
					_self.xingming=res.data.data.userName;
					_self.xingbie=res.data.data.schoolCode;
					_self.xuexiao=res.data.data.schoolCode;
					_self.zhuanye=res.data.data.userCode;
				}
			})
		},
		methods: {	
			}
		}
</script>
<style>
	.yangshi{
		display: flex;
		margin: 20upx;
	}
	.yangshi1{
		background:#007AFF;
		color: #FFFFFF;
		width: 30%;
		height: 80upx;
		font-size: 40upx;
		border-radius: 10upx;
		/* float: right; */
		margin-right: 20upx;
		text-align: center;
	}
	.yangshi2{
		/* background:#ffff8b; */
		color: #000000;
		width: 70%;
		height: 80upx;
		font-size: 40upx;
		border-radius: 10upx;
		border: 5upx solid #EEEEEE;
		/* float: right; */
	}
</style>
