
<template>
	<view>
		<view>
			
		</view>
		<view class="shangchuan">
		   <button  type="primary" @click="img">上传图片</button>
		</view>
		
		<view class="tijiao">
		   <button type="default" @click="submit">提交</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			img(){
			                uni.chooseImage({
			                    // count:  允许上传的照片数量
			                    count:5,
			                    // sizeType:  original 原图，compressed 压缩图，默认二者都有
			                    sizeType: "original",
			                    success(res){
			                        console.log(res)
			                        uni.previewImage({
			                            // 对选中的图片进行预览
			                            urls: res.tempFilePaths,
			                            // urls:['','']  图片的地址 是数组形式
			                        })
			                    } 
			                });
			            },
			
		}
	}
</script>

<style>
	.shangchuan{
		margin: 20upx;
		
		
	}
	.tijiao{
		margin: 20upx;
		
	}
</style>
