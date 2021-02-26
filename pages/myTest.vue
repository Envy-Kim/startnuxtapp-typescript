<template>
	<div class='inner'>
		<!-- tabs -->
		<tabs :items='tabItems'
			  :active='activeTab'
			  evClass='main-tab'
		>
			<!--
			슬롯 속성(slotProps)
			부모 컴포넌트에서 자식 컴포넌트의 슬롯에
			바인딩된 데이터에 접근하기 위하여 사용
			-->
			<template #title='{item, active}'>
				<!-- tab -->
				<tab :item='item' :active='active'
					 @input='changeMainTab'
				></tab>
			</template>
		</tabs>

		<!-- tab-items -->
		<tab-items :items='tabItems' :active='activeTab'>
			<template #event1='{item}'>
				<!-- tab-item -->
				<tab-item :item='item' :active='activeTab'>
					<!-- section1_1 -->
					<event-section :src="require('~/assets/images_aj/event1/ev1_kv.jpg')" />

					<!-- section1_2 -->
					<event-section :src="require('~/assets/images_aj/event1/ev1_step.jpg')" />

					<!-- section1_3 -->
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

					<!-- section1_4 -->
					<event-section :src="require('~/assets/images_aj/event1/ev1_prize.jpg')" />

					<!-- section1_5 -->
					<event-section :src="require('~/assets/images_aj/event1/ev1_join.jpg')">
						<btn class='btn-box bg-type'
							 btn-type='btn-entry'
							 width='360px'
							 left='330px'
							 bottom='100px'
							 @click.native='evStep01On = true'
						>응모하기
						</btn>

						<!-- event1 응모 step1 modal-->
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

						<!-- event1 응모 step2 modal-->
						<event-modal v-if='evStep02On' @close='closeModal'>
							<template #title>
								한우먹고!<i class='point'>한우인증 Go~!</i>
							</template>
							<template slot='sub-title'>
								경품 발송시 연락드릴 연락처를 입력해주세요.
								<i class='point'>한우 인증점 로고와
									<span>{{ (event1Data.type == 'examinee') ? '수험표가' : '영수증이' }}</span>
									나온 이미지를 업로드 후,<br>
									개인정보를 남겨주셔야 이벤트 참여가 완료됩니다.
								</i>
							</template>
							<template #content>
								<form>
									<div class='input-area'>
										<div class='flex-box'>
											<event-input
												id='cert_file_name'
												placeholder='이미지는 한장만 업로드 가능합니다.'
												styleType='m-file'
												:value='filename'
												disabled='true'
											/>
											<event-input input-type='file'
														 id='cert_file'
														 name='cert_file'
														 @input='setUploadFile'
											/>
										</div>
										<span class='info'>&#42; Jpg, Jpeg, Png 파일만 업로드 가능합니다.</span>
									</div>

									<event-input
										input-type='text'
										id='name'
										name='name'
										v-model='event1Data.name'
										placeholder='이름' />
									<event-input
										input-type='text'
										id='phone'
										name='phone'
										v-model='event1Data.phone'
										placeholder='전화번호' />
									<event-input
										input-type='text'
										id='email'
										name='email'
										v-model='event1Data.email'
										placeholder='이메일' />

									<aggrement padding-left='40px'>
										<template #checkbox>
											<event-input
												input-type='checkbox'
												name='ev1AggrChk1'
												id='ev1AggrChk1'
												v-model='event1Data.ev1AggrChk1'>
												<i class='point'>(필수)</i> 개인정보 활용 동의
											</event-input>
										</template>
										<template #detail_btn_text>자세히보기</template>
										<template #content>
											<p>개인정보 수집 동의</p>
											<p>
												1. 수집 항목 : [필수] 이름, 전화번호, 이메일<br />
												2. 수집 및 이용 목적 : 이벤트 참여<br />
												3. 업무 위탁 제공처 : 한우자조금관리위원회 위탁 협력업체<br />
												4. 보유 및 이용기간 : 해당 목적 달성 후 폐기
											</p>
										</template>
									</aggrement>

									<aggrement padding-left='20px'>
										<template #checkbox>
											<event-input
												input-type='checkbox'
												name='ev1AggrChk2'
												id='ev1AggrChk2'
												v-model='event1Data.ev1AggrChk2'>
												(선택) 마케팅 정보 수신 동의
											</event-input>
										</template>
										<template #detail_btn_text>자세히보기</template>
										<template #content>
											<p>마케팅 정보 수신 동의</p>
											<p>
												1. 수집 항목 : 이벤트 참여자 이름, 전화번호, 이메일<br />
												2. 수집 및 이용 목적 : 한우자조금관리위원회에서 진행하는 이벤트 및
												프로모션 안내<br />
												3. 업무 위탁 제공처 : 한우자조금관리위원회 위탁협력업체<br />
												4. 보유 및 이용기간 : 위탁 목적 및 계약 종료시까지<br />
												5. 동의 철회 방법 : 개인정보 보호 관리자 및 담당자에게 서면, 전화
												또는 이메일 연락
											</p>
										</template>
									</aggrement>

									<btn class='bg-type confirm-btn'
										 btn-type='btn-confirm'
										 width='280px'
										 @click.native='event01Submit'
									>확 인
									</btn>
								</form>
							</template>
						</event-modal>

						<!-- event1 응모 step3 modal-->
						<event-modal v-if='evStep03On' @close='closeModal'>
							<template #title>
								한우먹고!<i class='point'>한우인증 Go~!</i>
							</template>
							<template slot='sub-title'>
								이벤트 참여가 완료되었습니다.
							</template>
							<template #content>
								<btn class='bg-type confirm-btn'
									 btn-type='btn-confirm'
									 width='280px'
									 @click.native='closeModal'
								>확 인
								</btn>
							</template>
						</event-modal>
					</event-section>
				</tab-item>
			</template>

			<template #event2='{item}'>
				<!-- tab-item -->
				<tab-item :item='item' :active='activeTab'>
					<!-- section2_1 -->
					<event-section :src="require('~/assets/images_aj/event2/ev2_kv.jpg')" />

					<!-- section2_2 -->
					<event-section :src="require('~/assets/images_aj/event2/ev2_step.jpg')" />

					<!-- section2_3 -->
					<event-section class='ev2-bg-color'>
						<div class='list-wrap'>
							<!-- tabs -->
							<tabs :items='areaTabItem'
								  :active='areaActiveTab'
								  evClass='area-tab'
							>
								<template #title='{item, active}'>
									<!-- tab -->
									<tab :item='item' :active='active' @input='changeAreaTab' />
								</template>
							</tabs>

							<!-- tab-items -->
							<tab-items :items='areaTabItem' :active='areaActiveTab'>
								<template #area1='{item}'>
									<!-- tab-item -->
									<tab-item :item='item' :active='areaActiveTab'>
										<grid :items='storeList' />
									</tab-item>
								</template>

								<template #area2='{item}'>
									<!-- tab-item -->
									<tab-item :item='item' :active='areaActiveTab'>
										<grid :items='storeList' />
									</tab-item>
								</template>

								<template #area3='{item}'>
									<!-- tab-item -->
									<tab-item :item='item' :active='areaActiveTab'>
										{{ item }}
									</tab-item>
								</template>

								<template #area4='{item}'>
									<!-- tab-item -->
									<tab-item :item='item' :active='areaActiveTab'>
										{{ item }}
									</tab-item>
								</template>

								<template #area5='{item}'>
									<!-- tab-item -->
									<tab-item :item='item' :active='areaActiveTab'>
										{{ item }}
									</tab-item>
								</template>

								<template #area6='{item}'>
									<!-- tab-item -->
									<tab-item :item='item' :active='areaActiveTab'>
										{{ item }}
									</tab-item>
								</template>

								<template #area7='{item}'>
									<!-- tab-item -->
									<tab-item :item='item' :active='areaActiveTab'>
										{{ item }}
									</tab-item>
								</template>
							</tab-items>

							<btn btn-type='btn-more'
								 class='bg-type'
								 width='360px'
								 height='64px'
								 @click.native='evStep02On = true'
							>인증점 더보기
							</btn>

							<!-- event2 투표 step1 modal-->
							<event-modal v-if='evStep01On'
										 color-type='modal-pink'
										 @close='closeModal'>
								<template #title>
									내 마음 속의 <i class='point'>최애 한우인증점 Pick!</i>
								</template>
								<template #content>
									{{ storeList[0].title }}
								</template>
							</event-modal>

							<!-- event2 투표 step2 modal-->
							<event-modal v-if='evStep02On'
										 color-type='modal-pink'
										 @close='closeModal'>
								<template #title>
									내 마음 속의 <i class='point'>최애 한우인증점 Pick!</i>
								</template>
								<template slot='sub-title'>
									경품 발송시 연락드릴 연락처를 입력해주세요.
									<i class='point'>개인정보를 입력하시면 이벤트 참여가 완료됩니다.</i>
								</template>
								<template #content>
									<form>

										<div class='input-area'>
											<div class='flex-box'>
												<event-input
													input-type='radio'
													class='age-radio'
													id='radio1'
													name='radio'
													value='10'
													@input='setEventAge'
												>
													10대
												</event-input>
												<event-input
													input-type='radio'
													class='age-radio'
													id='radio2'
													name='radio'
													value='20'
													@input='setEventAge'
												>
													20대
												</event-input>
												<event-input
													input-type='radio'
													class='age-radio'
													id='radio3'
													name='radio'
													value='30'
													@input='setEventAge'
												>
													30대
												</event-input>
												<event-input
													input-type='radio'
													class='age-radio'
													id='radio4'
													name='radio'
													value='40'
													@input='setEventAge'
												>
													40대
												</event-input>
												<event-input
													input-type='radio'
													class='age-radio'
													id='radio5'
													name='radio'
													value='50'
													@input='setEventAge'
												>
													50대
												</event-input>
											</div>
										</div>


										<event-input
											input-type='text'
											id='name'
											name='name'
											v-model='event2Data.name'
											placeholder='이름' />
										<event-input
											input-type='text'
											id='phone'
											name='phone'
											v-model='event2Data.phone'
											placeholder='전화번호' />
										<event-input
											input-type='text'
											id='email'
											name='email'
											v-model='event2Data.email'
											placeholder='이메일' />

										<aggrement padding-left='40px'>
											<template #checkbox>
												<event-input
													input-type='checkbox'
													name='ev2AggrChk1'
													id='ev2AggrChk1'
													v-model='event2Data.ev2AggrChk1'>
													<i class='point'>(필수)</i> 개인정보 활용 동의
												</event-input>
											</template>
											<template #detail_btn_text>자세히보기</template>
											<template #content>
												<p>개인정보 수집 동의</p>
												<p>
													1. 수집 항목 : [필수] 이름, 전화번호, 이메일<br />
													2. 수집 및 이용 목적 : 이벤트 참여<br />
													3. 업무 위탁 제공처 : 한우자조금관리위원회 위탁 협력업체<br />
													4. 보유 및 이용기간 : 해당 목적 달성 후 폐기
												</p>
											</template>
										</aggrement>

										<aggrement padding-left='20px'>
											<template #checkbox>
												<event-input
													input-type='checkbox'
													name='ev2AggrChk2'
													id='ev2AggrChk2'
													v-model='event2Data.ev2AggrChk2'>
													(선택) 마케팅 정보 수신 동의
												</event-input>
											</template>
											<template #detail_btn_text>자세히보기</template>
											<template #content>
												<p>마케팅 정보 수신 동의</p>
												<p>
													1. 수집 항목 : 이벤트 참여자 이름, 전화번호, 이메일<br />
													2. 수집 및 이용 목적 : 한우자조금관리위원회에서 진행하는 이벤트 및
													프로모션 안내<br />
													3. 업무 위탁 제공처 : 한우자조금관리위원회 위탁협력업체<br />
													4. 보유 및 이용기간 : 위탁 목적 및 계약 종료시까지<br />
													5. 동의 철회 방법 : 개인정보 보호 관리자 및 담당자에게 서면, 전화
													또는 이메일 연락
												</p>
											</template>
										</aggrement>

										<btn class='bg-type confirm-btn'
											 btn-type='btn-confirm'
											 width='280px'
											 @click.native='event02Submit'
										>확 인
										</btn>
									</form>
								</template>
							</event-modal>

							<!-- event2 투표 step3 modal-->
							<event-modal v-if='evStep03On'
										 color-type='modal-pink'
										 @close='closeModal'>
								<template #title>
									내 마음 속의 <i class='point'>최애 한우인증점 Pick!</i>
								</template>
								<template slot='sub-title'>
									이벤트 참여가 완료되었습니다.
									<i class='point'>내일 다시 응모가 가능합니다.</i>
								</template>
								<template #content>
									<btn class='bg-type confirm-btn'
										 btn-type='btn-confirm'
										 width='280px'
										 @click.native='closeModal'
									>확 인
									</btn>
								</template>
							</event-modal>
						</div>
					</event-section>

					<!-- section2_4 -->
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
				</tab-item>
			</template>
		</tab-items>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue'
// 클래스 기반의 API를 사용하는 경우 공식 vue-class-component 데코레이터를 사용할 수 있음
// import Component from 'vue-class-component'

// vue-property-decorator는 vue-class-component를 기반으로 제작
// vuejs에서 typescript로 개발할 때, 클래스 컴포넌트 스타일의 개발을 도와주는 데코레이터들을 제공해주는 모듈
// @Component, @Prop, @Watch 등이 있음
import { Component } from 'vue-property-decorator'

export interface event1Data {
	type: string,
	name: string,
	phone: string,
	email: string,
	certFile: object,
	ev1AggrChk1: boolean,
	ev1AggrChk2: boolean
}

export interface event2Data {
	age: number,
	name: string,
	phone: string,
	email: string,
	comment: string,
	voteStore: number,
	ev2AggrChk1: boolean,
	ev2AggrChk2: boolean
}

/*
* @Component
* vuejs는 객체만을 처리
* Class를 객체로 만들어서 vuejs가 처리할 수 있도록 해줌
* */
@Component({
	layout: 'event'
})
export default class MyTest extends Vue {

	activeTab: number = 1
	tabItems: object[] = [
		{
			name: 'event1',
			key: 0,
			title: '',
			titlePoint: 'event1.',
			subTitle: '한우 먹고!',
			subTitlePoint: '한우 인증 GO~!'
		},
		{
			name: 'event2',
			key: 1,
			title: '',
			titlePoint: 'event2.',
			subTitle: '최애 한우인증점 Pick!',
			subTitlePoint: ''
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
		ev1AggrChk1: false,
		ev1AggrChk2: false
	}

	event2Data: event2Data = {
		age: 0,
		name: '',
		phone: '',
		email: '',
		comment: '',
		voteStore: 0,
		ev2AggrChk1: false,
		ev2AggrChk2: false
	}

	filename: string = ''

	areaActiveTab: number = 1
	areaTabItem: object[] = [
		{
			name: 'area1',
			key: 1,
			title: '전국'
		},
		{
			name: 'area2',
			key: 2,
			title: '수도권'
		},
		{
			name: 'area3',
			key: 3,
			title: '충청도'
		},
		{
			name: 'area4',
			key: 4,
			title: '전라도'
		},
		{
			name: 'area5',
			key: 5,
			title: '경상도'
		},
		{
			name: 'area6',
			key: 6,
			title: '강원도'
		},
		{
			name: 'area7',
			key: 7,
			title: '제주도'
		}
	]

	storeList: object[] = [
		{
			index: 1,
			title: '늘푸름 홍천 한우',
			img: require('~/assets/images_aj/event2/store/store_thum02.jpg')
		},
		{
			index: 2,
			title: '세종 한우',
			img: require('~/assets/images_aj/event2/store/store_thum02.jpg')
		},
		{
			index: 3,
			title: '모심정',
			img: require('~/assets/images_aj/event2/store/store_thum03.png')
		},
		{
			index: 4,
			title: '농업회사법인초원(주)안양지점',
			img: require('~/assets/images_aj/event2/store/store_thum04.png')
		},
		{
			index: 5,
			title: '다한우',
			img: require('~/assets/images_aj/event2/store/store_thum04.png')
		},
		{
			index: 6,
			title: '끼리 한우',
			img: require('~/assets/images_aj/event2/store/store_thum04.png')
		},
		{
			index: 7,
			title: '농업회사법인(주)포천한우백년',
			img: require('~/assets/images_aj/event2/store/store_thum07.png')
		},
		{
			index: 8,
			title: '강화섬약쑥한우',
			img: require('~/assets/images_aj/event2/store/store_thum08.png')
		},
		{
			index: 9,
			title: '늘푸름 홍천 한우',
			img: require('~/assets/images_aj/event2/store/store_thum09.jpg')
		}
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
			ev1AggrChk1: false,
			ev1AggrChk2: false
		}
		this.filename = ''

		this.event2Data = {
			age: 0,
			name: '',
			phone: '',
			email: '',
			comment: '',
			voteStore: 0,
			ev2AggrChk1: false,
			ev2AggrChk2: false
		}

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

		this.evStep01On = false
		this.evStep02On = false
		this.evStep03On = true
	}

	setUploadFile(files: any) {
		if (!files.length) {
			this.filename = ''
		} else {
			this.filename = files[0].name
		}
		this.event1Data.certFile = files
	}

	setEventAge(age: number) {
		this.event2Data.age = age
	}

	event02Submit() {
		console.log(this.event2Data)

		this.evStep01On = false
		this.evStep02On = false
		this.evStep03On = true
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
