<template>
	<div class='inner'>
		<!-- tab -->
		<tab
			:items="tabItems"
			:active="activeTab"
			@input='changeActiveTab'
		>
		</tab>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import Component from "vue-class-component";

@Component({
	layout: 'event/index'
})
export default class event extends Vue {

	activeTab: string = 'event1'

	tabItems = [
		{
			name: 'event1',
			sectionNum: 2,
			className: 'event1-class',
			subTitle: '한우 먹고!',
			subTitlePoint: '한우 인증 GO~!'
		},
		{
			name: 'event2',
			sectionNum: 3,
			className: 'event2-class',
			subTitle: '최애 한우인증점 Pick!',
			subTitlePoint: ''
		}
	]

	changeActiveTab(value: string) {
		console.log(value)
		this.activeTab = value
	}
}
</script>

<style scoped>
.inner {
	max-width: 1024px;
	margin: 0 auto;
}
</style>
