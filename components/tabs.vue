<template>
	<div class='tabs'>
		<ul class='tab' :class='evClass'>
			<template v-for="item of items">
				<!--
				범위가 있는 슬롯(Scoped Slots)
				자식 컴포넌트에서만 접근할 수 있는 데이터 중
				부모 컴포넌트의 슬롯에서 필요한 데이터를 제어, 랜더링하기 위해 사용.
				-->
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
