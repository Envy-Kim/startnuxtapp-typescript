<template>
	<li	:class="{ 'on': active === item.key }"
		@click="$emit('input', item.key)" >
		{{ item.title }}
		<i class="point">{{ item.titlePoint }}</i>
		{{ item.subTitle }}
		<i class="point" v-if="item.subTitlePoint">{{ item.subTitlePoint }}</i>
	</li>
</template>

<script lang='ts'>
import Vue from 'vue';
import { Component, Prop } from 'vue-property-decorator'

@Component
export default class Tab extends Vue {
	@Prop({default: []}) item?: object
	@Prop({default: 0}) active!: number
}
</script>

<style lang="scss" scoped>
@import "@/assets/scss/mixin";

.main-tab {
	li {
		display: flex;
		justify-content: center;
		align-items: center;
		width: 50%;
		height: 100%;
		font-family: 'BMJUA';
		font-size: 28px;
		color: #fff;
		border-radius: 20px 20px 0 0;
		background-color: #b3b3b3;
		cursor: pointer;
		&.on {
			color: #000;
			&:nth-child(1) {
				background-color: #ffdb6f;
				.point {
					color: #c83030;
				}
			}
			&:nth-child(2) {
				background-color: #f48585;
				.point {
					color: #feff9e;
				}
			}
		}
	}
}
.area-tab {
	li {
		width: calc( 100%/7 );
		height: 60px;
		font-size: 22px;
		color: #342c2b;
		background-color: $white;
		border-right: 1px solid #d3d3d3;
		&.on, &:hover {
			color: $white;
			font-weight: bold;
			border: none;
			background-color: #e4584b;
		}
		&:first-child {
			border-radius: 30px 0 0 30px;
		}
		&:last-child {
			border-radius: 0 30px 30px 0;
			border: none;
		}
	}
}
</style>
