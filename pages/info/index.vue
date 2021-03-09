<template>
	<view class="content">
		<view class="title">{{title}}</view>
		<view class="art-content">
			<rich-text :nodes="strings"></rich-text>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: '123',
				strings: ''
			}
		},
		onLoad(e) {
			console.log(e,222)
			uni.showLoading({
				title: '加载中。。。'
			})
			uni.request({
				url: `http://unidemo.dcloud.net.cn/api/news/36kr/${e.newsid}`,
				method: 'GET',
				data: {},
				success: res => {
					this.title = res.data.title;
					this.strings = res.data.content;
					uni.hideLoading();
				},
				fail: () => {
					
				},
				complete: () => {
					
				}
			})
		}
	}
</script>

<style>
.content {
	padding: 10upx 2%;
	width: 96%;
	flex-wrap: wrap;
}
.title {
	line-height: 2em;
	font-weight: 700;
	font-size: 38upx;
}
.art-content {
	line-height: 2em;
}
</style>
