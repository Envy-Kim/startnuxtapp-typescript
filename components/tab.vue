<template>
	<div>
		<ul class='tab'>
			<li v-for="(item, key) of items" :key="key">
				<nuxt-link v-if="active === key" class="on" @click.native="$emit('input', key)" to="">
					{{ item.name }}
				</nuxt-link>
				<nuxt-link v-else @click.native="$emit('input', key)" to="">
					{{ item.name }}
				</nuxt-link>
			</li>
		</ul>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import { Prop } from 'vue-property-decorator'
import Component from "vue-class-component";

@Component
export default class tab<T> extends Vue {
	@Prop({default: []}) items?: T[]
	@Prop() active!: number

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
				font-size: 0;
			}
		}
	}
</style>
