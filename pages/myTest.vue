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

	tabItems: object = [
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
					backImage: require('~/assets/images_aj/event1/ev1_kv.jpg'),
					class: '',
					btnYn: false,
				},
				{
					name: 'sec2',
					backImage: require('~/assets/images_aj/event1/ev1_step.jpg'),
					class: '',
					btnYn: false,
				},
				{
					name: 'sec3',
					backImage: require('~/assets/images_aj/event1/ev1_tmp_banner.jpg'),
					class: '',
					btnYn: true,
					left: '420px',
					bottom: '16px',
					btnType: "line-type",
					colorType: "color-yellow",
					width: "235px",
					btnText: "내 주변 한우 인증점 보러가기",
					subImgYn: true,
					subImg: require('~/assets/images_aj/event1/ico/ev1_ico_banner.png'),
					subImgClass: 'ico-banner',
				},
				{
					name: 'sec4',
					backImage: require('~/assets/images_aj/event1/ev1_prize.jpg'),
					class: '',
					btnYn: false,
				},
				{
					name: 'sec5',
					backImage: require('~/assets/images_aj/event1/ev1_join.jpg'),
					class: '',
					btnYn: true,
					left: '330px',
					bottom: '100px',
					btnType: "bg-type",
					funcType: "btn-entry",
					width: "360px",
					btnText: "응모하기"
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
					backImage: require('~/assets/images_aj/event2/ev2_kv.jpg'),
					class: '',
					btnYn: false,
				},
				{
					name: 'sec2',
					backImage: require('~/assets/images_aj/event2/ev2_step.jpg'),
					class: '',
					btnYn: false,
				},
				{
					name: 'sec3',
					backImage: require('~/assets/images_aj/event2/ev2_tmp1.jpg'),
					class: '',
					btnYn: false,
				},
				{
					name: 'sec3',
					backImage: 'none',
					class: 'ev2-bg-color',
				},
				{
					name: 'sec4',
					backImage: require('~/assets/images_aj/event2/ev2_tmp_banner.jpg'),
					class: '',
					btnYn: true,
					left: '370px',
					bottom: '16px',
					btnType: "line-type",
					colorType: "color-pink-white",
					width: "235px",
					btnText: "투표 현황 보러가기",
					subImgYn: true,
					subImg: require('~/assets/images_aj/event2/ico/ev2_ico_banner.png'),
					subImgClass: 'ico-banner',
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
