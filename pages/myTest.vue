<template>
	<div class='inner'>
		<!-- tab -->
		<tab
			:items='tabItems'
			:active='activeTab'
			evClass='main-tab'
			@input='changeMainTab'
		>
			<template #title >
					<tab-title></tab-title>
			</template>
		</tab>

	</div>
</template>

<script lang='ts'>
import Vue from 'vue'
import Component from 'vue-class-component'

export interface event1Data {
	type: string,
	name: string,
	phone: string,
	email: string,
	certFile: object,
	aggrchk1: boolean,
	aggrchk2: boolean
}

@Component({
	layout: 'event'
})
export default class MyTest extends Vue {

	activeTab: number = 1
	tabItems: object[] = [
		{
			name: 'event1',
			tabKey: 0,
			title: '',
			titlePoint: 'event1.',
			subTitle: '한우 먹고!',
			subTitlePoint: '한우 인증 GO~!',
			contents: [
				{ name: 'sec1' },
				{ name: 'sec2' },
				{ name: 'sec3' },
				{ name: 'sec4' },
				{ name: 'sec5' }
			]
		},
		{
			name: 'event2',
			tabKey: 1,
			title: '',
			titlePoint: 'event2.',
			subTitle: '최애 한우인증점 Pick!',
			subTitlePoint: '',
			contents: [
				{ name: 'sec1' },
				{ name: 'sec2' },
				{ name: 'sec3' },
				{ name: 'sec4' }
			]
		}
	]

	evStep01On: boolean = false
	evStep02On: boolean = false
	evStep03On: boolean = false
	applyType: string = 'public'

	event1Data: event1Data = {
		type: '',
		name: '',
		phone: '',
		email: '',
		certFile: {},
		aggrchk1: false,
		aggrchk2: false
	}

	filename: string = ""

	areaActiveTab: number = 1
	areaTabItem: object[] = [
		{
			name: 'area1',
			tabKey: 1,
			title: '전국',
			contents: [{ name: 'sec1' }]
		},
		{
			name: 'area2',
			tabKey: 2,
			title: '수도권',
			contents: [{ name: 'sec1' }]
		},
		{
			name: 'area3',
			tabKey: 3,
			title: '충청도',
			contents: [{ name: 'sec1' }]
		},
		{
			name: 'area4',
			tabKey: 4,
			title: '전라도',
			contents: [{ name: 'sec1' }]
		},
		{
			name: 'area5',
			tabKey: 5,
			title: '경상도',
			contents: [{ name: 'sec1' }]
		},
		{
			name: 'area6',
			tabKey: 6,
			title: '강원도',
			contents: [{ name: 'sec1' }]
		},
		{
			name: 'area7',
			tabKey: 7,
			title: '제주도',
			contents: [{ name: 'sec1' }]
		}
	]

	storeList: object[] = [
		{
			index: 1,
			title: '늘푸름 홍천 한우',
			img: require('~/assets/images_aj/event2/store/store_thum02.jpg'),
		},
		{
			index: 2,
			title: '세종 한우',
			img: require('~/assets/images_aj/event2/store/store_thum02.jpg'),
		},
		{
			index: 3,
			title: '모심정',
			img: require('~/assets/images_aj/event2/store/store_thum03.png'),
		},
		{
			index: 4,
			title: '농업회사법인초원(주)안양지점',
			img: require('~/assets/images_aj/event2/store/store_thum04.png'),
		},
		{
			index: 5,
			title: '다한우',
			img: require('~/assets/images_aj/event2/store/store_thum04.png'),
		},
		{
			index: 6,
			title: '끼리 한우',
			img: require('~/assets/images_aj/event2/store/store_thum04.png'),
		},
		{
			index: 7,
			title: '농업회사법인(주)포천한우백년',
			img: require('~/assets/images_aj/event2/store/store_thum07.png'),
		},
		{
			index: 8,
			title: '강화섬약쑥한우',
			img: require('~/assets/images_aj/event2/store/store_thum08.png'),
		},
		{
			index: 9,
			title: '늘푸름 홍천 한우',
			img: require('~/assets/images_aj/event2/store/store_thum09.jpg'),
		},
	]

	changeMainTab(value: number) {
		this.activeTab = value
	}
	changeAreaTab(value: number) {
		this.areaActiveTab = value
	}

	closeModal() {
		this.event1Data = {
			type: '',
			name: '',
			phone: '',
			email: '',
			certFile: [],
			aggrchk1: false,
			aggrchk2: false
		}
		this.filename = ''

		this.evStep01On = false
		this.evStep02On = false
		this.evStep03On = false
	}

	selectApplyType(type: string) {
		this.event1Data.type = type

		this.evStep01On = false
		this.evStep02On = true
		this.evStep03On = false
	}

	event01Submit() {
		console.log(this.event1Data)

		this.closeModal()
	}

	setUploadFile(files: any) {
		if (!files.length) {
			this.filename = ""
		}
		else {
			this.filename = files[0].name
		}
		this.event1Data.certFile = files
	}
}
</script>

<style lang='scss' scoped>
.inner {
	max-width: 1024px;
	margin: 0 auto;

	.list-wrap {
		padding: 0 55px 60px 55px;
	}
}

</style>
