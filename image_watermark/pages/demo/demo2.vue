<template>
	<view>
		<view id="content">
			<page-head :title="title"></page-head>
			<view class="uni-padding-wrap uni-common-mt">
				<view class="text" v-for="(num, index) in data" :key="index">list - {{ num }}</view>
				<view class="uni-loadmore" v-if="showLoadMore">{{ loadMoreText }}</view>
			</view>
		</view>
		<watermark type="follow" :height="wmheight + 'px'" :count="wmcount" :texts="texts" color="#1296db" logo="../../static/kxj-watermark/logo2.png"></watermark>
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
			count: 3, //每100px的水印数
			idstr: 'content', //内容容器id

			texts: ['涉密信息 禁止传播'],
			title: '下拉刷新 + 加载更多',
			data: [],
			loadMoreText: '加载中...',
			showLoadMore: false,
			max: 0
		};
	},
	onLoad() {
		this.initData();
	},

	onUnload() {
		(this.max = 0), (this.data = []), (this.loadMoreText = '加载更多'), (this.showLoadMore = false);
	},
	onReachBottom() {
		if (this.max > 40) {
			this.loadMoreText = '没有更多数据了!';
			return;
		}
		this.showLoadMore = true;
		setTimeout(() => {
			this.setListData();
		}, 300);
	},
	onPullDownRefresh() {
		console.log('onPullDownRefresh');
		this.initData();
	},
	methods: {
		//设置水印高度
		wmheightSet() {
			setTimeout(() => {
				var query = uni.createSelectorQuery().in(this);
				query
					.select('#' + this.idstr)
					.boundingClientRect(data => {
						console.log('得到布局位置信息' + JSON.stringify(data));
						this.wmheight = parseInt((data.height+40) / 100) * 100;
						this.wmcount = parseInt((data.height / 100) * this.count);
					})
					.exec();
			}, 300); //延时执行，不然节点还没渲染好，获取不到高度
		},

		initData() {
			setTimeout(() => {
				this.max = 0;
				this.data = [];
				let data = [];
				this.max += 10;
				for (var i = this.max - 9; i < this.max + 1; i++) {
					data.push(i);
				}
				this.data = this.data.concat(data);

				uni.stopPullDownRefresh();

				//数据发生改变时修改水印高度
				this.wmheightSet();
			}, 300);
		},
		setListData() {
			let data = [];
			this.max += 10;
			for (var i = this.max - 9; i < this.max + 1; i++) {
				data.push(i);
			}
			this.data = this.data.concat(data);

			//数据发生改变时修改水印高度
			this.wmheightSet();
		}
	}
};
</script>

<style>
.text {
	margin: 16rpx 0;
	width: 100%;
	background-color: #d9d9d9;
	height: 120rpx;
	line-height: 120rpx;
	text-align: center;
	color: #555;
	border-radius: 8rpx;
}

/* .fadein{
  transition: all 1.5s;
  opacity: 1;
} */

</style>
