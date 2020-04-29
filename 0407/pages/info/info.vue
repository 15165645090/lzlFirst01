<template>
	<view>
		{{news.data.noticeContent}}
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
			console.log(e);
			_self=this;
			_self.getNews(e);
		},
		methods: {
			getNews:function(a){
				uni.request({
					url:"http://192.168.1.143:8080/Notice/selectAll" ,
					method:"POST",
					header: {
						'content-type': 'application/x-www-form-urlencoded', 
					},
					success:function(res){
				 		console.log(res);
						_self.news=res.data;  	
					}
					})
			}
			
		}
	}	
</script>

<style>

</style>
