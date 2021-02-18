<template>
	<div class='inner'>
		<!-- tab -->
			<tabtest
				:items="tabItems"
				:active="activeTab"
				@input='changeActiveTab'
			>
			</tabtest>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import Component from "vue-class-component";

@Component
export default class myTest extends Vue {
	activeTab: string = 'event1'

	tabItems = [
		{
			name: 'event1',
			sectionNum: 2,
			className: 'event1-class'
		},
		{
			name: 'event2',
			sectionNum: 3,
			className: 'event2-class'
		}
	]

	event1TabImg: string = require('~/assets/images/event1/ev1_tmp1.jpg')
	event1Img1: string = require('~/assets/images/event1/ev1_kv.jpg')
	event1Img3: string = require('~/assets/images/event1/ev1_tmp_banner.jpg')
	event1Img5: string = require('~/assets/images/event1/ev1_join.jpg')
	event1FootImg = require('~/assets/images/event1/ev1_ft.jpg')

	event2TabImg: string = require('~/assets/images/event2/ev2_tmp2.jpg')
	event2Img1: string = require('~/assets/images/event2/ev2_kv.jpg')
	event2Img4: string = require('~/assets/images/event2/ev2_tmp_banner.jpg')
	event2FootImg = require('~/assets/images/event2/ev2_ft.jpg')


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
