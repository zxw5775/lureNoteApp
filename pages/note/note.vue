<template>
	<view class="note-header">
		<view class="flex flex-center padding-horizontal-16">
			<bing-countup color="#4F9F60" splitorColor="#4F9F60" :font-size="28"></bing-countup>
			<view class="spacer"></view>
			<lure-button type="primary" @click="handleBack">返回</lure-button>
			<!-- <button size="mini" type="primary" @click="handleBack">返回</button> -->
		</view>
		<view class="flex padding-horizontal-16">
			<uni-icons type="compose" size="20"></uni-icons>
			<input placeholder="点击输入本次路亚标题" class="margin-left-8" />
		</view>
		<view class="note-container-top"></view>
	</view>
	<scroll-view class="note-container">
		1111
		111
		111
		111
		111
		111
		
	</scroll-view>
	<!-- 中鱼 -->
	<uni-fab :pattern="pattern" horizontal="right" @fabClick="handleAdd"></uni-fab>
	<lure-popup v-model="dialog">
		aaaa
	</lure-popup>
</template>

<script setup>
	import { ref } from 'vue';
	import {
	    onHide,
	    onShow
	  } from "@dcloudio/uni-app";

	// 返回
	const handleBack = () => {
		uni.switchTab({
			url:"/pages/calendar/index"
		})
	}
	
	/**
	 * 中鱼
	 */
	const pattern = {
		buttonColor: '#4F9F60'
	}
	const dialog = ref(false);
	const handleAdd = ()=> {
		dialog.value = true;
	}
	
	// 生命周期
	onShow(()=> {
		console.log('onShow')
		uni.hideTabBar()
	})
	onHide(()=> {
		console.log('onHide')
		uni.showTabBar()
	})
</script>

<style lang="scss" scoped>
	:deep(.uni-icons) {
		color: #fff !important;
	}
	.note-header {
		background-color: #222222;
		.note-container-top {
			height: 20px;
			margin-top: 12px;
			background-color: #28272C;
			border-radius: 20px 20px 0 0;
		}
	}
</style>
