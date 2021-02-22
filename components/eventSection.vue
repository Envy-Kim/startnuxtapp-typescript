<template>
	<div class="ev-section" :class="secClass" >
		<img v-if="src != 'none'" :src="src" alt="" />
		<slot></slot>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import {Component, Prop} from "vue-property-decorator";

@Component
export default class eventSection extends Vue {
	@Prop({default: ''}) src?: string
	@Prop({default: ''}) secClass?: string
}
</script>

<style lang="scss">

.ico-banner {
	position: absolute;
	bottom: 0;
	left: 230px;
}

.ev-section {
	position: relative;
}

.ev2-bg-color {
	background-color: #ffeaec;
}
</style>
