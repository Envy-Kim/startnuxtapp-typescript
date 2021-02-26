<template>
	<div>
		<div v-for="item of items">
			<slot :name="item.name" :item="item" />
		</div>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue'
import { Component, Prop } from 'vue-property-decorator'

@Component
export default class TabItems extends Vue {
	@Prop({default: []}) items?: object
	@Prop({default: 0}) active!: number
}
</script>

<style scoped>
</style>
