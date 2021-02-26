<template>
	<ul>
		<li v-for="(item, index) of items" :key='item.index' >
			<slot name='content' :item='item' />
		</li>
	</ul>
</template>

<script lang='ts'>
import Vue from 'vue'
import { Component, Prop } from 'vue-property-decorator'

@Component
export default class Grid extends Vue {
	@Prop({default : 3}) maxRow?: number
	@Prop({default : 3}) maxCol?: number
	@Prop({default: []}) items?: object

}
</script>

<style lang='scss' scoped>
@import "@/assets/scss/mixin";

ul {
	display: flex;
	flex-wrap: wrap;
	justify-content: center;
	li {
		margin: auto auto 25px auto;
	}
}
</style>
