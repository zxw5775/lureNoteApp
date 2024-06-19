<template>
	<uni-popup ref="popup" type="bottom">
		<view class="lure-popup-container">
			<view class="lure-popup_content">
				<view class="lure-popup-header flex">
					<view v-if="title">{{title}}</view>
					<view class="spacer"></view>
					<uni-icons type="close" size="28" @click="handleClose"></uni-icons>
				</view>
				<slot></slot>
				<view class="footer">
					
				</view>
			</view>
		</view>
	</uni-popup>
</template>

<script lang="ts" setup>
import { computed, ref, watch } from 'vue';

const props = withDefaults(defineProps<{
	modelValue: boolean;
	title?: string;
	showClose?: boolean; //是否显示关闭按钮
	showFooter?: boolean; //是否显示底部操作区域

	// footer button
	cancelLoading?: boolean; // 取消按钮加载状态
	confirmLoading?: boolean; // 确认按钮加载状态
	cancelDisabled?: boolean; // 取消按钮是否为禁用状态
	confirmDisabled?: boolean; // 确认按钮是否为禁用状态
	showCancelButton?: boolean; // 是否显示取消按钮
	showConfirmButton?: boolean; // 是否显示确认按钮
	cancelButtonText?: string; // 取消按钮的文本内容
	confirmButtonText?: string; // 确认按钮的文本内容
	cancelButtonClass?: string; // 取消按钮的自定义类名
	confirmButtonClass?: string; // 确认按钮的自定义类名
}>(), {
	showClose: true,
	showFooter: true,
	showCancelButton: true,
	showConfirmButton: true,
});

const emit = defineEmits([
  "update:modelValue",
  "open",
  "opened",
  "close",
  "closed",
  "cancelOnClick",
  "confirmOnClick",
]);

const popup = ref()
watch(() => props.modelValue, (newValue)=> {
	if (newValue) {
		popup.value.open();
	} else {
		popup.value.close();
	}
})

// 关闭
const handleClose = () => {
	emit("update:modelValue", false)
	popup.value.close();
	emit('closed')
}
</script>

<style lang="scss">
:deep(.uni-icons) {
	color: #fff !important;
}
.lure-popup-container {
	height: 100vh;
	background-color: var(--background-color);
	.lure-popup_content {
		padding: 50px 12px 12px;
		
	}
}
</style>