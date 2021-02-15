<template>
	<div>
		<li v-for="(item, key) of items" :key="key">
			<nuxt-link v-if="active === key" class="on" @click.native="$emit('input', key)" to="">{{item.name}}</nuxt-link>
			<nuxt-link v-else @click.native="$emit('input', key)" to="">{{ item.name }}</nuxt-link>
		</li>
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

<style scoped>

</style>
