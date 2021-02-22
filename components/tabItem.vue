<template>
	<div>
		<div v-for="section of contents">
			<event-section :src="section.backImage" :secClass="section.class">
				<img
					v-if="section.subImgYn"
					:src="section.subImg"
					:class="section.subImgClass" />

				<btn v-if="section.btnYn"
					 :btn-type="section.btnType"
					 :funcType="section.funcType"
					 :colorType="section.colorType"
					 :width="section.width"
					 :height="section.height"
					 :left="section.left"
					 :bottom="section.bottom"
				>{{ section.btnText }}</btn>
			</event-section>
		</div>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import { Component, Prop } from 'vue-property-decorator'

@Component
export default class tabItem extends Vue {
	@Prop({default: []}) contents!: object
}
</script>

<style lang="scss" scoped>
.ico-banner {
	position: absolute;
	bottom: 0;
	left: 230px;
}
</style>
