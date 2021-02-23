<template>
	<div>
		<div v-for="(item) of items">
			<div v-for="(section, index) of item.contents">
				<slot v-if="(item.name == active)"
					  :name="item.name + '_' + (index+1)" />
			</div>
		</div>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import { Component, Prop } from 'vue-property-decorator'

@Component
export default class TabItem extends Vue {
	@Prop({default: []}) items?: object
	@Prop() active!: string
}
</script>

<style lang="scss" scoped>
.ico-banner {
	position: absolute;
	bottom: 0;
	left: 230px;
}
</style>
