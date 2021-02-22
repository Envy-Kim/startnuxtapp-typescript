<template>
	<div>
		<div class='tabs'>
			<ul class='tab' >
				<li v-for="item of items"
					:class="{ 'on': active === item.name }"
					@click="$emit('input', item.name)"
				>
					{{ item.title }}
					<i class="point">{{ item.titlePoint }}</i>
					{{ item.subTitle }}
					<i class="point" v-if="item.subTitlePoint">{{ item.subTitlePoint }}</i>
				</li>
			</ul>
		</div>

		<div v-for="(item) of items" class='tab-item'>
			<tab-item v-if="(item.name == active)"  :contents='item.contents'>


			</tab-item>
		</div>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import { Prop } from 'vue-property-decorator'
import Component from "vue-class-component";

@Component
export default class tab extends Vue {
	@Prop({default: []}) items?: any
	@Prop() active!: string

	mounted() {
		console.log(this.items)
	}
}
</script>

<style lang="scss" scoped>
@import "@/assets/scss/mixin";

ul {
	display: flex;
	justify-content: center;
	align-items: center;
	width: 100%;
	height: 60px;
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
</style>
