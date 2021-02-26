<template>
	<p><slot /></p>
</template>

<script lang='ts'>
import Vue from 'vue'
import {Component} from 'vue-property-decorator'

@Component
export default class CardTitle extends Vue {
}
</script>

<style lang='scss' scoped>
	p {
		align-self: stretch;
		width: 100%;
		font-size: 22px;
		margin-left: 10px;
		color: #3e2e2f;
		font-weight: bold;
	}
</style>
