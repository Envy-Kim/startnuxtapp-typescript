<template>
	<div>
		<slot />
	</div>
</template>

<script lang='ts'>
import Vue from 'vue'
import { Component } from 'vue-property-decorator'

@Component
export default class Pagenate extends Vue {
}
</script>

<style lang='scss' scoped>

</style>
