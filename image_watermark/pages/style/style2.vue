<template>
	<view style="overflow-x: hidden ;">
		<!--页面信息内容-->
		<view id="common" class="uni-padding-wrap uni-common-mt">
			<view class="content">
				<image class="logo" src="/static/logo.png"></image>
				<view class="text-area">
					<text class="title">页面内容水印</text>
				</view>
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

		<!--水印容器-->
		<view class="watermarks" :style="{height:myheight}">
			<block v-for="(t, i) in count" :key="'concise'+i">
				<!--简洁样式，只有一行-->
				<view class="concise">
					<image src="../../static/kxj-watermark/logo2.png" style="width:26rpx;height: 26rpx;float: left;"></image>
					<view class="wmtext" style="padding-left: 30rpx;">涉密信息 禁止传播</view>
				</view>
			</block>
			<block v-for="(t, i) in count" :key="'standard'+i">
				<!--标准样式，有三行-->
				<view class="standard">
					<image src="../../static/kxj-watermark/logo2.png" style="width:64rpx;height: 64rpx;float: left;"></image>
					<view style="padding-left: 66rpx;">
						<view class="wmtext" >涉密信息 禁止传播</view>
						<view class="wmtext" >张三 管理员 189******16</view>
						<view class="wmtext" >2020-08-14 16:46:39</view>
					</view>
				</view>
			</block>
		</view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			count: 18, //水印密度
			myheight:'0px'
		};
	},
	onReady(){
		var query = uni.createSelectorQuery().in(this);
		query.select('#common').boundingClientRect(data => {
		  console.log("得到布局位置信息" + JSON.stringify(data));
		  this.myheight = data.height+20+'px';
		  console.log(this.myheight)
		}).exec();
	},
	methods: {
		
	}
};
</script>

<style lang="scss">


//水印样式
$wm-fontsize: 26rpx; //文字大小
$wm-rotate: -35deg; //旋转角度
$wm-opacity: 0.8; //透明度

.watermarks {
	position: absolute;
	z-index: 996;
	display: flex;
	flex-wrap: wrap;
	pointer-events: none;
	width: 150%;
	
	top: 0;
	left: 0;
	
	right: 0;
	overflow-x: hidden ;

	opacity: $wm-opacity;
	
	.wmtext {
		color: #d9d9d9;
		font-size: $wm-fontsize;
		line-height: $wm-fontsize;
	}
	
	.concise {
		
		transform: rotate($wm-rotate);
		
	}

	.standard {
		
		transform: rotate($wm-rotate);
		.wmtext {
			color: #1296db;
			}
	}

	
}

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
