<template>
	<div class='card'>
		<nuxt-link to="">
			<img v-if="img !== ''" :src="img" alt="">
		</nuxt-link>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import { Component, Prop } from 'vue-property-decorator'

@Component
export default class Card extends Vue{
	@Prop({default: ''}) img?: string

}
</script>

<style lang="scss" scoped>

@import "@/assets/scss/mixin";

.card {
	width: 270px;
	height: 310px;
	margin-bottom: 25px;
	border-radius: 30px;
	background-color: #fff;
	box-shadow: 5px 5px 0 rgba(246,218,220);
	overflow: hidden;
	a {
		display: block;
		width: 100%;
		height: 100%;
	}
	.info {
		display: flex;
		flex-wrap: wrap;
		align-items: flex-end;
		height: 130px;
		padding: 20px 15px;
		p {
			align-self: stretch;
			width: 100%;
			font-size: 22px;
			margin-left: 10px;
			color: #3e2e2f;
			font-weight: bold;
		}
	}
}

</style>
