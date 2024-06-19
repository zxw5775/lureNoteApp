<template>
	<component class="lure-checkcard-group">
		<slot></slot>
	</component>
</template>

<script lang="ts">
export type CheckcardGroupValueType = Exclude<CheckboxValueType, boolean>[]
const props = defineProps({
/**
 * @description binding value
 */
modelValue: {
    type: Array<any>,
    default: () => [],
},


</script>

<style lang="scss">

</style>