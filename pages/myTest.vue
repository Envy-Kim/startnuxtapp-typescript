<template>
	<div class='inner'>
		<!-- tab -->
		<tab
			:items="tabItems"
			:active="activeTab"
			@input='changeActiveTab'
		>
			<tab-item :items='tabItems' :active="activeTab">
				<!-- event1 -->
				<template #event1_1>
					<event-section :src="require('~/assets/images_aj/event1/ev1_kv.jpg')">
					</event-section>
				</template>
				<template #event1_2>
					<event-section :src="require('~/assets/images_aj/event1/ev1_step.jpg')">
					</event-section>
				</template>
				<template #event1_3>
					<event-section :src="require('~/assets/images_aj/event1/ev1_tmp_banner.jpg')">
						<img :src="require('~/assets/images_aj/event1/ico/ev1_ico_banner.png')"
							 class="ico-banner" />
						<btn btn-type='line-type'
							 colorType='color-yellow'
							 width='235px'
							 left='420px'
							 bottom='16px'
						>내 주변 한우 인증점 보러가기</btn>
					</event-section>
				</template>
				<template #event1_4>
					<event-section :src="require('~/assets/images_aj/event1/ev1_prize.jpg')">
					</event-section>
				</template>
				<template #event1_5>
					<event-section :src="require('~/assets/images_aj/event1/ev1_join.jpg')">
						<btn btn-type='bg-type'
							 funcType='btn-entry'
							 width='360px'
							 left='330px'
							 bottom='100px'
							 @click.native='test'
						>응모하기
						</btn>
					</event-section>
				</template>

				<!-- event2 -->
				<template #event2_1>
					<event-section :src="require('~/assets/images_aj/event2/ev2_kv.jpg')">
					</event-section>
				</template>
				<template #event2_2>
					<event-section :src="require('~/assets/images_aj/event2/ev2_step.jpg')">
					</event-section>
				</template>
				<template #event2_3>
					<event-section :src="require('~/assets/images_aj/event2/ev2_tmp1.jpg')">
					</event-section>
				</template>
				<template #event2_4>
					<event-section :src="require('~/assets/images_aj/event2/ev2_tmp_banner.jpg')">
						<btn btn-type='line-type'
							 colorType='color-pink-white'
							 width='235px'
							 left='370px'
							 bottom='16px'
						>투표 현황 보러가기</btn>
					</event-section>
				</template>
			</tab-item>
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
			tabType: 'text',
			title: '',
			titlePoint: 'event1.',
			subTitle: '한우 먹고!',
			subTitlePoint: '한우 인증 GO~!',
			contents: [
				{name: 'sec1'},
				{name: 'sec2'},
				{name: 'sec3'},
				{name: 'sec4'},
				{name: 'sec5'}
			]
		},
		{
			name: 'event2',
			tabType: 'text',
			title: '',
			titlePoint: 'event2.',
			subTitle: '최애 한우인증점 Pick!',
			subTitlePoint: '',
			contents: [
				{name: 'sec1'},
				{name: 'sec2'},
				{name: 'sec3'},
				{name: 'sec4'}
			]
		}
	]


	changeActiveTab(value: string) {
		console.log(value)
		this.activeTab = value
	}
	test() {
		alert('test')
	}
}
</script>

<style scoped>
.inner {
	max-width: 1024px;
	margin: 0 auto;
}
</style>
