<template>
	<div class='inner'>
		<!-- tab -->
		<v-img :src='(activeTab === 0 ? event1TabImg : event2TabImg)'>
			<tab
				:items="tabItems"
				:active="activeTab"
				@input='changeActiveTab'
			>
			</tab>
		</v-img>

		<!-- 본문 -->
		<div v-show='activeTab === 0'>
			<v-img :src='event1Img1'></v-img>
			<v-img :src='event1Img2'></v-img>
			<v-img :src='event1Img3'>
				<div>
					<img src='~/assets/images/event1/ico/ev1_ico_banner.png'>
				</div>

			</v-img>
			<v-img :src='event1Img4'></v-img>
			<v-img :src='event1Img5'></v-img>
			<v-img :src='event1FootImg'></v-img>
		</div>
		<div v-show='activeTab === 1'>
			<v-img :src='event2Img1' ></v-img>
			<v-img :src='event2Img2' ></v-img>
			<v-img :src='event2Img3' ></v-img>
			<v-img :src='event2Img4' ></v-img>
			<v-img :src='event2FootImg'></v-img>
		</div>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import Vuetify from 'vuetify'
import Component from "vue-class-component";

Vue.use(Vuetify)

@Component
export default class myTest extends Vue {
	activeTab: number = 0

	tabItems = [
		{
			name: 'event1',
		},
		{
			name: 'event2',
		}
	]

	event1TabImg: string = require('~/assets/images/event1/ev1_tmp1.jpg')
	event1Img1: string = require('~/assets/images/event1/ev1_kv.jpg')
	event1Img2: string = require('~/assets/images/event1/ev1_step.jpg')
	event1Img3: string = require('~/assets/images/event1/ev1_tmp_banner.jpg')
	event1Img4: string = require('~/assets/images/event1/ev1_prize.jpg')
	event1Img5: string = require('~/assets/images/event1/ev1_join.jpg')
	event1FootImg = require('~/assets/images/event1/ev1_ft.jpg')

	event2TabImg: string = require('~/assets/images/event2/ev2_tmp2.jpg')
	event2Img1: string = require('~/assets/images/event2/ev2_kv.jpg')
	event2Img2: string = require('~/assets/images/event2/ev2_step.jpg')
	event2Img3: string = require('~/assets/images/event2/ev2_tmp1.jpg')
	event2Img4: string = require('~/assets/images/event2/ev2_tmp_banner.jpg')
	event2FootImg = require('~/assets/images/event2/ev2_ft.jpg')


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
</style>
