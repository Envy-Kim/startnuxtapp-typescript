<template>
	<div class='grid'>
		<div v-for="(row, index) of getGridData()" class='row'>
			<div v-for="(col, key) of row" class="col">
				<card :img="col.img" >
					<card-title>{{ col.title }}</card-title>
					<btn btn-type='line-type'
						 colorType='color-pink'
						 width='235px'
					>컨텐츠보고 투표 GO</btn>
				</card>
			</div>
		</div>
	</div>

<!--	<ul>-->
<!--		<li v-for="(item, index) of items" :key='item.index'-->
<!--			:class="{'li-row-end': (index+1) % maxCol === 0}">-->
<!--			{{ (index+1) / maxCol }} {{ maxRow }} {{ gridColumn }}-->
<!--			<card-->
<!--				v-if="(index+1) % maxCol < maxRow"-->
<!--				:img="item.img" >-->
<!--				<card-title>{{ item.title }}</card-title>-->
<!--				<btn btn-type='line-type'-->
<!--					 colorType='color-pink'-->
<!--					 width='235px'-->
<!--				>컨텐츠보고 투표 GO</btn>-->
<!--			</card>-->
<!--		</li>-->
<!--	</ul>-->
<!--		<li>-->
<!--			<card :img="require('~/assets/images_aj/event2/store/store_thum02.jpg')" >-->
<!--				<card-title>세종한우</card-title>-->
<!--				<btn btn-type='line-type'-->
<!--					 colorType='color-pink'-->
<!--					 width='235px'-->
<!--				>컨텐츠보고 투표 GO</btn>-->
<!--			</card>-->
<!--		</li>-->
<!--		<li>-->
<!--			<card :img="require('~/assets/images_aj/event2/store/store_thum02.jpg')" >-->
<!--				<card-title>세종한우</card-title>-->
<!--				<btn btn-type='line-type'-->
<!--					 colorType='color-pink'-->
<!--					 width='235px'-->
<!--				>컨텐츠보고 투표 GO</btn>-->
<!--			</card>-->
<!--		</li>-->
<!--		<li>-->
<!--			<card :img="require('~/assets/images_aj/event2/store/store_thum02.jpg')" >-->
<!--				<card-title>세종한우</card-title>-->
<!--				<btn btn-type='line-type'-->
<!--					 colorType='color-pink'-->
<!--					 width='235px'-->
<!--				>컨텐츠보고 투표 GO</btn>-->
<!--			</card>-->
<!--		</li>-->
<!--		<li>-->
<!--			<card :img="require('~/assets/images_aj/event2/store/store_thum02.jpg')" >-->
<!--				<card-title>세종한우</card-title>-->
<!--				<btn btn-type='line-type'-->
<!--					 colorType='color-pink'-->
<!--					 width='235px'-->
<!--				>컨텐츠보고 투표 GO</btn>-->
<!--			</card>-->
<!--		</li>-->
<!--		<li>-->
<!--			<card :img="require('~/assets/images_aj/event2/store/store_thum02.jpg')" >-->
<!--				<card-title>세종한우</card-title>-->
<!--				<btn btn-type='line-type'-->
<!--					 colorType='color-pink'-->
<!--					 width='235px'-->
<!--				>컨텐츠보고 투표 GO</btn>-->
<!--			</card>-->
<!--		</li>-->
<!--		<li>-->
<!--			<card :img="require('~/assets/images_aj/event2/store/store_thum02.jpg')" >-->
<!--				<card-title>세종한우</card-title>-->
<!--				<btn btn-type='line-type'-->
<!--					 colorType='color-pink'-->
<!--					 width='235px'-->
<!--				>컨텐츠보고 투표 GO</btn>-->
<!--			</card>-->
<!--		</li>-->
<!--	</ul>-->
</template>

<script lang='ts'>
import Vue from 'vue'
import {Component, Prop} from 'vue-property-decorator'

@Component
export default class Grid extends Vue {
	@Prop({default : 3}) maxRow?: number
	@Prop({default : 3}) maxCol?: number
	@Prop({default: []}) items?: object

	// gridData: object = {
	// 	row1: [
	// 		{
	// 			index: 1,
	// 			title: '늘푸름 홍천 한우',
	// 			img: require('~/assets/images_aj/event2/store/store_thum02.jpg'),
	// 		},
	// 		{
	// 			index: 2,
	// 			title: '세종 한우',
	// 			img: require('~/assets/images_aj/event2/store/store_thum02.jpg'),
	// 		},
	// 		{
	// 			index: 3,
	// 			title: '모심정',
	// 			img: require('~/assets/images_aj/event2/store/store_thum02.jpg'),
	// 		},
	// 	],
	// 	row2: [
	// 		{
	// 			index: 4,
	// 			title: '농업회사법인초원(주)<br>안양지점',
	// 			img: require('~/assets/images_aj/event2/store/store_thum02.jpg'),
	// 		},
	// 		{
	// 			index: 5,
	// 			title: '다한우',
	// 			img: require('~/assets/images_aj/event2/store/store_thum02.jpg'),
	// 		},
	// 		{
	// 			index: 6,
	// 			title: '끼리 한우',
	// 			img: require('~/assets/images_aj/event2/store/store_thum02.jpg'),
	// 		},
	// 	],
	// 	row3: [
	// 		{
	// 			index: 7,
	// 			title: '농업회사법인(주)<br>포천한우백년',
	// 			img: require('~/assets/images_aj/event2/store/store_thum02.jpg'),
	// 		},
	// 		{
	// 			index: 8,
	// 			title: '강화섬약쑥한우',
	// 			img: require('~/assets/images_aj/event2/store/store_thum02.jpg'),
	// 		},
	// 		{
	// 			index: 9,
	// 			title: '늘푸름 홍천 한우',
	// 			img: require('~/assets/images_aj/event2/store/store_thum02.jpg'),
	// 		},
	// 	],
	// }

	gridData: object = {}

	getGridData() {
		this.gridData.row = [
			{
				index: 7,
				title: '농업회사법인(주)포천한우백년',
				img: require('~/assets/images_aj/event2/store/store_thum02.jpg'),
			},
			{
				index: 8,
				title: '강화섬약쑥한우',
				img: require('~/assets/images_aj/event2/store/store_thum02.jpg'),
			},
			{
				index: 9,
				title: '늘푸름 홍천 한우',
				img: require('~/assets/images_aj/event2/store/store_thum02.jpg'),
			},
		]

		console.log(this.gridData)
		return this.gridData
	}
}
</script>

<style lang='scss' scoped>
@import "@/assets/scss/mixin";

ul {
	display: flex;
	flex-wrap: wrap;
	justify-content: center;
	li {
		margin-bottom: 25px;
		margin-right: 25px;

		&.li-row-end {
			margin-right: 0;
		}
	}

}

.grid {
	display: flex;
	flex-wrap: wrap;
	justify-content: center;
	.row {
		margin-bottom: 25px;
	}
}
</style>
