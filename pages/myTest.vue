<template>
	<div>
		<!-- tab -->
		<tab
			:items="tabItems"
			:active="activeTab"
			@input='changeActiveTab2'
		></tab>

		<!-- 본문 -->
		<div v-if='activeTab === 0'>
			test
		</div>
		<div v-else-if='activeTab === 1'>
			test2
		</div>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import Component from "vue-class-component";

@Component
export default class myTest extends Vue {
	activeTab: number = 0

	tabItems = [
		{name: 'event1'},
		{name: 'event2'}
	]

	changeActiveTab2(value: number) {
		console.log(value)
		this.activeTab = value
	}
}
</script>

<style scoped>

</style>
