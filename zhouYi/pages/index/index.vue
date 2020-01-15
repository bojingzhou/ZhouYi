<template>
	<view class="box">
		<view class=" a">
			<view class="a-t left">
				<view class="a-t-l">
					<svg class="icon" aria-hidden="true">
						<use xlink:href="#icon-yi"></use>
					</svg>
				</view>
				<view class="a-t-r left">
					<view v-for="(item,index) in yi" :key="index">{{item}}</view>
				</view>
			</view>
			<view class="a-b left">
				<view class="a-b-l">
					<svg class="icon" aria-hidden="true">
						<use xlink:href="#icon-ji"></use>
					</svg>
				</view>
				<view class="a-b-r left">
					<view v-for="(item,index) in ji" :key="index">{{item}}</view>
				</view>
			</view>
		</view>
		<view class="b center">
			<view>{{yangli}}</view>
			<view>{{yingli}}</view>
		</view>
		<view class="c between">
			<view class="left">{{chong}}</view>
			<view class="left">{{sha}}</view>
			<view class="left">{{wuxing}}</view>
		</view>
		<view class="d center">
			<view>{{caishen}}</view>
			<view>{{xishen}}</view>
			<view>{{fushen}}</view>
		</view>
		<view class="e">
			<view class="left">{{suici}}</view>
			<view class="left">{{xiongshen}}</view>
			<view class="left">{{jishenyiqu}}</view>
		</view>
	</view>
</template>

<script>
	import {
		url
	} from '../../common/config.js'
	export default {
		data() {
			return {
				yi: "",
				ji: "",
				yangli: "",
				yingli: "",
				chong: "",
				sha: "",
				wuxing: "",
				caishen: "",
				xishen: "",
				fushen: "",
				taishen: "",
				suici: "",
				xiongshen: "",
				jishenyiqu: ""
			}
		},
		onLoad() {

		},
		onReady() {
			this.getData();
		},
		methods: {
			getData() {
				let that = this;
				uni.request({
					url: url, //仅为示例，并非真实接口地址。
					data: {
						dataType: "json",
					},

					success: function(res) {
						let data = JSON.parse(res.data).result;
						that.yi = data.yi;
						that.ji = data.ji
						that.yangli = data.yangli
						that.yingli = data.nongli
						that.chong = data.chong
						that.sha = data.sha
						that.wuxing = data.wuxing
						that.caishen = data.caishen
						that.xishen = data.xishen
						that.fushen = data.fushen
						that.taishen = data.taishen
						that.suici = data.suici.join(",")
						that.xiongshen = data.xiongshen
						that.jishenyiqu = data.jishenyiqu

					}
				});
			}
		}
	}
</script>

<style lang="scss">
	.box {
		box-sizing: border-box;
		padding: 30rpx;
		font-size: 28rpx;
		background-color: #e8e7e7;
	}

	.a>view {
		padding: 20rpx;
	}

	.a-t {
		background: #e2e2e2;
		color: #1ec509;
	}

	.a-b {
		background: #e2e2e2;
		color: red;
		margin-top: 20rpx;
	}

	.a-t-l,
	.a-b-l {
		width: 40rpx;
		height: 40rpx;
		margin-right: 30rpx;
	}

	.a-t-r,
	.a-b-r {
		flex: 1;
		display: flex;
		flex-wrap: wrap;
	}

	.a-t-r view,
	.a-b-r view {
		margin: 10rpx
	}

	.b {
		margin-top: 20rpx;
	}

	.b>view {
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 20rpx;
		border-radius: 10rpx;
		// background-color: #e4e4e4;
	}

	.b>view:first-child:before,
	.b>view:last-child:before {
		color: red;
		font-weight: bold;
		margin-bottom: 10rpx;
	}

	.b>view:last-child {
		margin-left: 40rpx;
	}

	.b>view:first-child:before {
		content: "阳历";
	}

	.b>view:nth-child(2):before {
		content: "阴历";
	}

	.c {
		margin-top: 30rpx;
	}

	.c>view:first-child:before,
	.c>view:nth-child(2):before,
	.c>view:last-child:before {
		margin-right: 20rpx;
		font-weight: bold;
		color: red;
	}

	.c>view:first-child:before {
		content: "冲";
	}

	.c>view:nth-child(2):before {
		content: "煞";
	}

	.c>view:last-child:before {
		content: "五行";
	}

	.d {
		margin-top: 40rpx;
	}

	.d>view {
		display: flex;
		flex-direction: column;
		align-items: center;
		margin: 20rpx;
	}

	.d>view:first-child:before,
	.d>view:nth-child(2):before,
	.d>view:last-child:before {
		font-weight: bold;
		color: red;
	}

	.d>view:first-child:before {
		content: "财神";
	}

	.d>view:nth-child(2):before {
		content: "喜神";
	}

	.d>view:nth-child(3):before {
		content: "福神";
	}

	.e>view {

		margin-top: 40rpx;
	}

	.e>view:first-child:before,
	.e>view:nth-child(2):before,
	.e>view:nth-child(3):before {
		font-weight: bold;
		color: red;
		margin-right: 20rpx;
	}

	.e>view:first-child:before {
		content: "岁次";
	}

	.e>view:nth-child(2):before {
		content: "凶神";
	}

	.e>view:nth-child(3):before {
		content: "吉神";
	}
</style>
