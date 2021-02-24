<template>
	<div class='card' :style="{'width':width, 'height': height}">
		<nuxt-link to="">
			<img v-if="img !== ''" :src="img" alt="">

			<div class="info">
				<slot />
			</div>
		</nuxt-link>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import { Component, Prop } from 'vue-property-decorator'

@Component
export default class Card extends Vue{
	@Prop({default: ''}) img?: string
	@Prop({default: '270px'}) width?: string
	@Prop({default: '310px'}) height?: string

}
</script>

<style lang="scss" scoped>

@import "@/assets/scss/mixin";

.card {
	margin: 0 auto;
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
	}
}

</style>
