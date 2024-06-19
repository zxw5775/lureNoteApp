<template>
	<view class="container">
		我是首页
		<button @click="goTo('')" type="primary" size="mini">去日历</button>
	</view>
</template>

<script setup>
	
	const goTo = (url)=> {
		uni.navigateTo({
			url: '/pages/note/note'
		})
	}
</script>

<style lang="scss" >
	$uni-bg-color-hover: red;
	.container {
		padding: 20px;
		font-size: 14px;
		line-height: 24px;
	}
</style>
