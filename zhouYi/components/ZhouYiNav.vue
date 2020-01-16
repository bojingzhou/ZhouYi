<template>
	<view>
		<view class="h" :style="{'background-color':bac}">{{title}}</view>
	</view>
</template>

<script>
	export default {
		props: ['title', 'bac'],
		data() {
			return {

			};
		},
		created() {}
	}
</script>

<style>
	.h {
		color: #fff;
		text-align: center;
		height: 88rpx;
		line-height: 88rpx;
		padding-top: 40rpx;
		font-size: 32rpx;
	}
</style>
