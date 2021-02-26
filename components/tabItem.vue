<template>
	<div v-show="item.key === active">
		<slot />
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import { Component, Prop } from 'vue-property-decorator'

@Component
export default class TabItem extends Vue {
	@Prop({default: []}) item?: object
	@Prop() active!: number
}
</script>

<style lang="scss" scoped>
</style>
