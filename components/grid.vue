<template>
	<!--
	todo : component와 슬롯에 대해 조금 더 고민 후 수정
	-->
	<ul>
		<li v-for="(item, index) of items" :key='item.index' >
			<card
				:img="item.img"
				width='270px'>
				<card-title>{{ item.title }}</card-title>
				<btn btn-type='line-type'
					 colorType='color-pink'
					 width='235px'
				>컨텐츠보고 투표 GO</btn>
			</card>
		</li>
	</ul>
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

}
</script>

<style lang='scss' scoped>
@import "@/assets/scss/mixin";

ul {
	display: flex;
	flex-wrap: wrap;
	justify-content: center;
	li {
		margin: auto auto 25px auto;
	}
}
</style>
