<template>
    <view>
       <view class="uni-title uni-common-pl"></view>
        <view class="uni-list">
            <view class="uni-list-cell">
                <view class="uni-list-cell-left">
                    活动名称：
                </view>
                <view class="uni-list-cell-db">
                    <picker @change="bindPickerChange" :value="index" :range="array">
                        <view class="uni-input">{{array[index]}}</view>
                    </picker>
                </view>
            </view>
        </view>
		
		<view class="uni-padding-wrap">
			<view class="uni-title">类型：</view>
			<view class="qiandao">
				<image src='../../static/login/saoyisao.png' mode="widthFix" @click="saomiao"></image>
			    <label class="radio"><button type="primary" @click="tel()">签到</button></label>
			</view>
			<view >
				<label class="radio"><button type="primary" @click="tel()">签退</button></label>
			</view>
			
		</view>
		<br/><br/>
		
    </view>
</template>

<script>
	export default {
	    data() {
	        const currentDate = this.getDate({
	            format: true
	        })
	        return {
	            title: 'picker',
	            array: ['活动1', '活动2', '活动3', '活动4'],
	            index: 0,
	            date: currentDate,
	            time: '12:01'
	        }
	    },
	    computed: {
	        startDate() {
	            return this.getDate('start');
	        },
	        endDate() {
	            return this.getDate('end');
	        }
	    },
	    methods: {
			tel:function(){
			                uni.scanCode({
			                    success:function(res){
			                        console.log(JSON.stringify(res.result));
			                    }
			                });
			            },
	        bindPickerChange: function(e) {
	            console.log('picker发送选择改变，携带值为', e.target.value)
	            this.index = e.target.value
	        },
			saomiao:function(){
				uni.scanCode({
				    onlyFromCamera: true,
				    success: function (res) {
				        console.log('条码类型：' + res.scanType);
				        console.log('条码内容：' + res.result);
				    }
				})
			}
	       
	        
			
	    }
	}
</script>

<style>
	.qiandao{display: flex;padding: 20rpx;}
	.qiandao image{width: 10%;margin-top: 10rpx;margin-right: 20rpx;}
	
</style>