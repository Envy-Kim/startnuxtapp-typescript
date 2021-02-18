<template>
	<div>
		<div class='tabs'>
			<ul class='tab' >
				<li v-for="item of items">
					<nuxt-link :class="{ 'on': active === item.name }" @click.native="$emit('input', item.name)" to="">
						{{ item.name }}
					</nuxt-link>
				</li>
			</ul>
		</div>

		<div class='tab-item-group'>
			<div v-for="(item) of items" class='tab-item'>
				<tab-item v-if="(item.name == active)" :item='item'></tab-item>
			</div>
		</div>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import { Prop } from 'vue-property-decorator'
import Component from "vue-class-component";

@Component
export default class tabtest extends Vue {
	@Prop({default: []}) items?: Object
	@Prop() active!: string

	mounted() {
		console.log(this.items)
	}
}
</script>

<style lang='scss' scoped>
	li {list-style: none;}
	.tab {
		position: absolute;
		left: 0;
		right: 0;
		display: flex; justify-content: center; align-items: center;

		li {
			width: 50%; height: 60px;

			a {
				display: block;
				height: 100%;
				//font-size: 0;
			}
		}
	}
</style>
