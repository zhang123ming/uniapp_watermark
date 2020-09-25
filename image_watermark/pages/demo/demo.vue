<template>
	<view style="overflow-x: hidden ;">
		<!--页面信息内容-->
		<view id="content" class="uni-padding-wrap uni-common-mt">
			<view class="content">
				<image class="logo" src="/static/logo.png"></image>
				<view class="text-area"><text class="title">页面内容水印</text></view>
			</view>
			<view class="uni-title uni-common-mt">
				更多布局示例
				<text>\nflex布局演示</text>
			</view>
			<view>
				<view class="uni-hello-text">
					Flex是Flexible Box的缩写，意为“弹性布局”，用来为盒状模型提供最大的灵活性。当设置display: flex后，继续给view等容器组件设置flex-direction:
					row或column，就可以在该容器内按行或列排布子组件。uni-app推荐使用flex布局。因为flex布局有利于跨更多平台，尤其是采用原生渲染的平台。
				</view>
			</view>
		</view>
		<watermark type="follow" :height="wmheight + 'px'" color="#1296db" logo="../../static/kxj-watermark/logo2.png"></watermark>
	</view>
</template>

<script>
import watermark from '../../components/kxj-watermark/kxj-watermark.vue';
export default {
	components: { watermark }, //注册插件
	data() {
		return {
			wmheight: 0,
			wmcount: 0,
			count: 2, //每100px的水印数
			idstr: 'content' //内容容器id
		};
	},
	onReady() {
		
		//页面完成后需要手动指定页面节点的整体高度
		var query = uni.createSelectorQuery().in(this);
		query.select('#'+this.idstr).boundingClientRect(data => {
			this.wmheight = parseInt((data.height+40) / 100) * 100;
			this.wmcount = parseInt((data.height / 100) * this.count);
		}).exec();
	}
};
</script>

<style lang="scss">
//页面内容样式
@import '../../common/uni.css';
.flex-item {
	width: 33.3%;
	height: 200rpx;
	text-align: center;
	line-height: 200rpx;
}

.flex-item-V {
	width: 100%;
	height: 150rpx;
	text-align: center;
	line-height: 150rpx;
}

.text {
	margin: 15rpx 10rpx;
	padding: 0 20rpx;
	background-color: #ebebeb;
	height: 70rpx;
	line-height: 70rpx;
	text-align: center;
	color: #777;
	font-size: 26rpx;
}
.content {
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
}

.logo {
	height: 200rpx;
	width: 200rpx;
	margin-top: 200rpx;
	margin-left: auto;
	margin-right: auto;
	margin-bottom: 50rpx;
}

.text-area {
	display: flex;
	justify-content: center;
}

.title {
	font-size: 36rpx;
	color: #8f8f94;
}
</style>
