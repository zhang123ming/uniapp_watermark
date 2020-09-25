<template>
	<view>
		<view style="text-align: center;padding: 20rpx;">
			<image src="../../static/screenshot.png" style="width: 700rpx;height: 700rpx;">
			<text style="color: #999999;">-----效果截图，如上-----</text>
		</view>
		<view class="uni-padding-wrap uni-common-mt">
			<navigator url="../demo/demo" open-type="navigate" class="text">水印Demo</navigator>
		</view>
		<view class="uni-padding-wrap uni-common-mt">
			<navigator url="../demo/demo1" open-type="navigate" class="text">水印Demo-固定</navigator>
		</view>
		<view class="uni-padding-wrap uni-common-mt">
			<navigator url="../demo/demo2" open-type="navigate" class="text">水印Demo-随动</navigator>
		</view>
		<view class="uni-padding-wrap uni-common-mt">
			<navigator url="../demo/demo3" open-type="navigate" class="text">更多样式效果</navigator>
		</view>
	</view>
</template>
<script>
	
	export default {
		
		data() {
			return {
				
			}
		},
		onLoad() {
			
		},
		
		
		methods: {
			
		}
	}
</script>

<style>
	.text {
		margin: 16rpx 0;
		width:100%;
		border: #1296db 1px solid;
		height: 100rpx;
		line-height: 100rpx;
		text-align: center;
		color: #1296db;
		border-radius: 8rpx;
	}
</style>
