<template>
	<div class='tabs'>
		<ul class='tab' :class='evClass'>
			<template v-for="item of items">
				<slot name="title" :item='item' :active='active' />
			</template>
		</ul>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import { Component, Prop } from 'vue-property-decorator'

@Component
export default class Tabs extends Vue {
	@Prop({default: []}) items?: object
	@Prop({default: 0}) active!: number
	@Prop({default: ''}) evClass?: string
}
</script>

<style lang="scss" scoped>
@import "@/assets/scss/mixin";

.tabs {
	ul {
		display: flex;
		li {
			display: inline-flex;
			justify-content: center;
			align-items: center;
			cursor: pointer;
		}
	}
	.main-tab {
		justify-content: center;
		align-items: center;
		width: 100%;
		height: 60px;
	}
	.area-tab {
		width: 910px;
		height: 60px;
		border-radius: 30px;
		box-shadow: 5px 5px 0 rgba(0,0,0,.1);
		padding-bottom: 60px;
	}
}
</style>
