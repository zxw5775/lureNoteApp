<template>
	<view class="lure-button-container">
		<button :class="`lure-button__${type} lure-button__${size} lure-button`" @click="emit('click')"><slot /></button>
	</view>
</template>

<script setup lang="ts">
/**
 * lure Button
 * @description 钓记按钮 组件
 * 
 * @tutorial 
 * 
 * @property {String} type 类型 [primary, default]
 * @property {String} size 文字大小 [mini, default, large]
 * @example <lure-button></lure-button>
 */

const props = withDefaults(defineProps<{
	type: string;
	size?: string;
}>(), {
	type: 'default',
	size: ''
});

const emit = defineEmits(['click']);
</script>

<style lang="scss">
	.lure-button {
		padding-left: 16px;
		padding-right: 16px;
		font-size: 14px;
		border-radius: 20px;
	}
	.lure-button__mini{
		font-size: 12px;
		line-height: 2.2;
	}
	.lure-button__default {
		
	}
	.lure-button__primary {
		background-color: var(--color-primary);
		color: var(--color-white);
	}
</style>