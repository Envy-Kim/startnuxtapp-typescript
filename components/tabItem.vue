<template>
	<div>
		<div v-for="section of contents">
			<event-section :src="section.backImage" :secClass="section.class">
				<sub-img :src="section.subImg" />
				<btn v-if="section.btnYn" :btn-type="section.btnType"></btn>
			</event-section>
		</div>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import { Component, Prop } from 'vue-property-decorator'

@Component
export default class tabItem extends Vue {
	@Prop({default: []}) contents: Object
}
</script>

<style lang="scss" scoped>
</style>
