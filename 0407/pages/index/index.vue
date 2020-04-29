<template>
	<view >
		<navigator class="news-list" :url="'../info/info?id='+item.noticeCode" v-for="(item,index) in news" >
			<image src="../../static/login/1.png" mode="widthFix"></image>
			<view class="news-title">{{item.noticeTitle}}</view> 
		</navigator>
	</view>
		
	
</template>

<script>
	var _self
	export default {
		data() {
			return{			
				news :[]
			}
		},
		onLoad:function(e){
			_self=this;
			_self.getNews();
			
			
			
		},
		methods: {
				
			getNews:function(){
				uni.request({
					url:"http://192.168.1.143:8080/Notice/selectAll",
					method:"POST",
					header: {
						'content-type': 'application/x-www-form-urlencoded', 
					},
					success:function(res){
				 		console.log(res);
						_self.news=res.data.data;  	
					}
					})
				
			}
			
		}
	}
</script>

<style>
	.news-list{ display: flex;  width: 94%;padding: 10upx 3%;}
	.news-list image{width: 100upx;margin-right:50upx;}
	.news-title{width: 100%;margin-top: 12upx;height: auto;} 
	swiper-item { background-color: #007AFF;height: 200px;width: 100%; color: #FFFFFF;}
</style>
