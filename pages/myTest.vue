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
export default class myTest extends Vue {

	activeTab: string = 'event1'

	event1Img1: string = require('~/assets/images_bak/event1/ev1_kv.jpg')
	event1Img2: string = require('~/assets/images_bak/event1/ev1_step.jpg')
	event1Img3: string = require('~/assets/images_bak/event1/ev1_tmp_banner.jpg')
	event1Img4: string = require('~/assets/images_bak/event1/ev1_prize.jpg')
	event1Img5: string = require('~/assets/images_bak/event1/ev1_join.jpg')

	event2Img1: string = require('~/assets/images_bak/event2/ev2_kv.jpg')
	event2Img2: string = require('~/assets/images_bak/event2/ev2_step.jpg')
	event2Img3: string = require('~/assets/images_bak/event2/ev2_tmp1.jpg')
	event2Img4: string = require('~/assets/images_bak/event2/ev2_tmp_banner.jpg')

	tabItems = [
		{
			name: 'event1',
			className: 'event1-class',
			titleType: 'text',
			title: '',
			titlePoint: 'event1.',
			subTitle: '한우 먹고!',
			subTitlePoint: '한우 인증 GO~!',
			contents: [
				{
					name: 'sec1',
					backImage: this.event1Img1,
					class: '',
					btnYn: false,
				},
				{
					name: 'sec2',
					backImage: this.event1Img2,
					class: '',
					btnYn: false,
				},
				{
					name: 'sec3',
					backImage: this.event1Img3,
					class: '',
					btnYn: false,
				},
				{
					name: 'sec4',
					backImage: this.event1Img4,
					class: '',
					btnYn: false,
				},
				{
					name: 'sec5',
					backImage: this.event1Img5,
					class: '',
					btnYn: false,
				}
			]
		},
		{
			name: 'event2',
			className: 'event2-class',
			titleType: 'text',
			title: '',
			titlePoint: 'event2.',
			subTitle: '최애 한우인증점 Pick!',
			subTitlePoint: '',
			contents: [
				{
					name: 'sec1',
					backImage: this.event2Img1,
					class: '',
					btnYn: false,
				},
				{
					name: 'sec2',
					backImage: this.event2Img2,
					class: '',
					btnYn: false,
				},
				{
					name: 'sec3',
					backImage: this.event2Img3,
					class: '',
					btnYn: false,
				},
				{
					name: 'sec3_1',
					backImage: 'none',
					class: 'ev2-bg-color',
					btnYn: true,
					btnType: 'more-btn',
				},
				{
					name: 'sec4',
					backImage: this.event2Img4,
					class: '',
					btnYn: false,
				}
			]
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
