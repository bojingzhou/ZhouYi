<template>
	<view class="box">
		<ZhouYiNav bac="red" title="易友圈"></ZhouYiNav>
		<scroll-view class="scroll-view_H" scroll-x="true">
			<view @click="tabClick(index)" class="scroll-view-item_H " :class="num==index?'active':''" :id="index" v-for="(item,index) in tabArr"
			 :key="index">{{item.name}}</view>
		</scroll-view>

		<swiper class="swiper con" @change='change' :current="num">
			<swiper-item>
				<scroll-view scroll-y="true" class="scroll-Y" @scrolltoupper="upper" @scrolltolower="lower" >
					<view class="xx" @touchstart="start" @touchend="end" @touchmove="move" style="height: 1500rpx;background-color: #C0C0C0;"
					 :style="{'transform': 'translateY('+moveH+')'}">{{moveH}}</view>
				</scroll-view>
			</swiper-item>
			<swiper-item>
				<scroll-view scroll-y="true" class="scroll-Y" @scrolltoupper="upper" @scrolltolower="lower" >
					<view>2</view>
				</scroll-view>
			</swiper-item>
			<swiper-item>
				<scroll-view scroll-y="true" class="scroll-Y" @scrolltoupper="upper" @scrolltolower="lower" >
					<view>3</view>
				</scroll-view>
			</swiper-item>
			<swiper-item>
				<scroll-view scroll-y="true" class="scroll-Y" @scrolltoupper="upper" @scrolltolower="lower" >
					<view>4</view>
				</scroll-view>
			</swiper-item>
		</swiper>
	</view>

</template>

<script>
	import {
		url
	} from '../../common/config.js';
	import ZhouYiNav from '../../components/ZhouYiNav';
	export default {
		components: {
			ZhouYiNav
		},
		data() {
			return {
				num: 0,
				tabArr: [{
					name: "网友心愿"
				}, {
					name: "最多祝福"
				}, {
					name: "我的许愿"
				}, {
					name: "我的评论"
				}],
				startY: 0,
				moveY: 0,
				endY: 0,
				moveH: 0
			}
		},
		onLoad() {

		},
		onReady() {},
		methods: {
			upper() {},
			lower() {},
			tabClick(index) {
				this.num = index
			},
			change(event) {
				this.num = event.detail.current
			},
			start(e) {
				this.startY = e.touches[0].pageY;
			},
			move(e) {
				console.log(e.touches[0])
				this.moveY = e.touches[0].pageY;
				this.moveH = (this.moveY - this.startY) + "px";
				console.log(this.moveH)
			},
			end(e) {
				this.moveH = "0px";
			}
		}
	}
</script>

<style lang="scss">
	uni-page-body,
	uni-page-refresh,
	.box {
		height: 100%;
	}

	.box {
		display: flex;
		flex-direction: column;
	}


	.scroll-view_H {
		color: #fff;
		background-image: linear-gradient(#ff0000, #ef8582);
		white-space: nowrap;
		width: 100%;
		font-size: 30rpx;
	}

	.scroll-view-item_H {
		font-weight: bold;
		box-sizing: border-box;
		width: 25%;
		text-align: center;
		padding: 10rpx 20rpx;
		display: inline-block;
	}

	.active {
		color: #ffb300;
	}

	.con {
		flex: 1;

	}

	.scroll-Y {
		box-sizing: border-box;
		padding: 0rpx 30rpx;
		height: 100%;
	}

	.scroll-Y>view {
		transition: all ease 2s;
	}

	.scroll-view-item {
		height: 600rpx;
	}
</style>
