<template>
	<div class='inner'>
		<!-- tab -->
		<!-- v-img : vuetify의 이미 만들어진 컴포넌트 -->
		<v-img :src='(activeTab === 0 ? event1TabImg : event2TabImg)'>
			<!-- v-bind를 이용한 동적인 prop 전달 -->
			<!-- @{이벤트명} 을 이용하여 자식 컴포넌트에서 emit한 이벤트에 대한 처리를 설정 -->
			<old-tab
				:items="tabItems"
				:active="activeTab"
				:active2="activeTab2"
				@input='changeActiveTab'
			>
			</old-tab>
		</v-img>

		<!-- 본문 -->
		<div v-show='activeTab === 0'>
			<v-img :src='event1Img1'></v-img>
			<v-img :src='event1Img2'></v-img>
			<v-img :src='event1Img3'>
				<div class='banner-img'>
					<img src='~/assets/images_aj/event1/ico/ev1_ico_banner.png'>
				</div>
			</v-img>
			<v-img :src='event1Img4'></v-img>
			<v-img :src='event1Img5'></v-img>
			<v-img :src='event1FootImg'></v-img>
		</div>
		<div v-show='activeTab === 1'>
			<v-img :src='event2Img1'></v-img>
			<v-img :src='event2Img2'></v-img>
			<v-img :src='event2Img3'></v-img>
			<v-img :src='event2Img33'>
				<btn btnType='more-btn' >인증점 더보기</btn>
			</v-img>
			<v-img :src='event2Img4'>
				<div class='banner-img'>
					<img src='~/assets/images_aj/event2/ico/ev2_ico_banner.png'>
				</div>
			</v-img>
			<v-img :src='event2FootImg'></v-img>
		</div>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import Component from "vue-class-component";

// @Component 데코레이터는 클래스가 Vue 컴포넌트임을 나타냅니다
@Component
export default class index extends Vue {
	activeTab: number = 1
	activeTab2: string = 'event1'

	tabItems = [
		{
			name: 'event1',
		},
		{
			name: 'event2',
		}
	]

	event1TabImg: string = require('~/assets/images_aj/event1/ev1_tmp1.jpg')
	event1Img1: string = require('~/assets/images_aj/event1/ev1_kv.jpg')
	event1Img2: string = require('~/assets/images_aj/event1/ev1_step.jpg')
	event1Img3: string = require('~/assets/images_aj/event1/ev1_tmp_banner.jpg')
	event1Img4: string = require('~/assets/images_aj/event1/ev1_prize.jpg')
	event1Img5: string = require('~/assets/images_aj/event1/ev1_join.jpg')
	event1FootImg = require('~/assets/images_aj/event1/ev1_ft.jpg')

	event2TabImg: string = require('~/assets/images_aj/event2/ev2_tmp2.jpg')
	event2Img1: string = require('~/assets/images_aj/event2/ev2_kv.jpg')
	event2Img2: string = require('~/assets/images_aj/event2/ev2_step.jpg')
	event2Img3: string = require('~/assets/images_aj/event2/ev2_tmp1.jpg')
	event2Img33: string = require('~/assets/images_aj/event2/ev2_tmp3.jpg')
	event2Img4: string = require('~/assets/images_aj/event2/ev2_tmp_banner.jpg')
	event2FootImg = require('~/assets/images_aj/event2/ev2_ft.jpg')

	changeActiveTab(value: number) {
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
.banner-img {

}
</style>
