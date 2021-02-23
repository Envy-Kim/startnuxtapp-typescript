<template>
	<div class='inner'>
		<!-- tab -->
		<tab
			:items='tabItems'
			:active='activeTab'
			@input='changeActiveTab'
		/>

		<tab-item :items='tabItems' :active='activeTab'>
			<!-- event1 Start -->
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
						 class='ico-banner' />
					<btn class='btn-box'
						 btn-type='line-type'
						 colorType='color-yellow'
						 width='235px'
						 left='420px'
						 bottom='16px'
					>내 주변 한우 인증점 보러가기
					</btn>
				</event-section>
			</template>

			<template #event1_4>
				<event-section :src="require('~/assets/images_aj/event1/ev1_prize.jpg')">
				</event-section>
			</template>

			<template #event1_5>
				<event-section :src="require('~/assets/images_aj/event1/ev1_join.jpg')">
					<btn class='btn-box bg-type'
						 btn-type='btn-entry'
						 width='360px'
						 left='330px'
						 bottom='100px'
						 @click.native='evStep01On = true'
					>응모하기
					</btn>

					<event-modal v-if='evStep01On' @close='closeModal'>
						<template #title>
							한우먹고!<i class='point'>한우인증 Go~!</i>
						</template>
						<template slot='sub-title'>
							수험생과 일반 참여 방법이 다릅니다!<br>참여 유형을 선택해주세요.
						</template>
						<template #content>
							<ul class='select'>
								<li @click="selectApplyType('examinee')">수험생으로 참여할꺼에요!</li>
								<li @click="selectApplyType('public')">일반으로 참여할꺼에요!</li>
							</ul>
						</template>
					</event-modal>

					<event-modal v-if='evStep02On' @close='closeModal'>
						<template #title>
							한우먹고!<i class='point'>한우인증 Go~!</i>
						</template>
						<template slot='sub-title'>
							경품 발송시 연락드릴 연락처를 입력해주세요.
							<i class='point'>한우 인증점 로고와
								<span>{{ (applyType == 'examinee') ? '수험표가' : '영수증이' }}</span> 나온 이미지를 업로드 후,<br>
								개인정보를 남겨주셔야 이벤트 참여가 완료됩니다.
							</i>
						</template>
						<template #content>
							<div class='input-area'>
								<div class='flex-box'>
									<vue-input
										placeholder='이미지는 한장만 업로드 가능합니다.' />
								</div>
								<span class='info'>&#42; Jpg, Jpeg, Png 파일만 업로드 가능합니다.</span>
							</div>
							<vue-input
								placeholder='이름' />
							<vue-input
								placeholder='전화번호' />
							<vue-input
								placeholder='이메일' />

							<vue-agreement><i class='point'>(필수)</i> 개인정보 활용 동의</vue-agreement>
							<vue-agreement>(선택) 마케팅 정보 수신 동의</vue-agreement>

							<btn class='bg-type confirm-btn'
								 btn-type='btn-confirm'
								 width='280px'
								 @click.native='event01Submit'
							>확 인
							</btn>
						</template>
					</event-modal>
				</event-section>
			</template>
			<!-- event1 End -->

			<!-- event2 Start -->
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
					<img :src="require('~/assets/images_aj/event2/ico/ev2_ico_banner.png')"
						 class='ico-banner' />
					<btn class='btn-box'
						 btn-type='line-type'
						 colorType='color-pink-white'
						 width='235px'
						 left='370px'
						 bottom='16px'
					>투표 현황 보러가기
					</btn>
				</event-section>
			</template>
			<!-- event2 End -->
		</tab-item>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue'
import Component from 'vue-class-component'

@Component({
	layout: 'event/index'
})
export default class Event extends Vue {

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
				{ name: 'sec1' },
				{ name: 'sec2' },
				{ name: 'sec3' },
				{ name: 'sec4' },
				{ name: 'sec5' }
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


	changeActiveTab(value: string) {
		console.log(value)
		this.activeTab = value
	}

	closeModal() {
		this.evStep01On = false
		this.evStep02On = false
		this.evStep03On = false
	}

	selectApplyType(type: string) {
		this.applyType = type

		this.evStep01On = false
		this.evStep02On = true
		this.evStep03On = false
	}

	event01Submit() {
		this.evStep01On = false
		this.evStep02On = false
		this.evStep03On = true
	}
}
</script>

<style scoped>
.inner {
	max-width: 1024px;
	margin: 0 auto;
}
</style>
