<template>
	<view class="uni-padding-wrap uni-common-mt">
		
		<view class="content" style="text-align: center;">
			<image class="logo" src="/static/logo.png" ></image>
			<view class="text-area">
				<text class="title">更多样式效果</text>
			</view>
			
		</view>
		
		
		<watermark color="#c7254e" logo="../../static/logo.png" :texts="['涉密信息 禁止传播','这里是第二行的内容']"></watermark>
	</view>
</template>
<script>
	import watermark  from "../../components/kxj-watermark/kxj-watermark.vue"
	export default {
		components: { watermark}, //注册插件
		data() {
			return {}
		}
	}
</script>

<style>
	@import url("../../common/uni.css");
	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}
	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
