<template>
	<div>
		{{item.name}}
		<p>{{item}}</p>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import { Component, Prop } from 'vue-property-decorator'

@Component
export default class tabItem extends Vue {
	@Prop({default: []}) item?: Object
}
</script>

<style scoped>

</style>
