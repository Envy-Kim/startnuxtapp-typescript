<template>
	<div class='btn-box'>
		<div v-if="btnType === 'default'">
			<button >default</button>
		</div>
		<div v-if="btnType === 'more-btn'" :class='btnType'>
			<nuxt-link to="">
				<img src='~/assets/images/common/ico/ico_tmp02.png'></img>
				<span>인증점 더보기</span>
			</nuxt-link>
		</div>

		<div v-if="btnType === 'detail-btn'" :class='btnType'>
			<button>detail</button>
		</div>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import Component from "vue-class-component";
import { Prop } from 'vue-property-decorator'

@Component
export default class btn extends Vue {
	@Prop({default: 'default'}) btnType: string

}
</script>

<style lang='scss' scoped>
	.more-btn {
		position: absolute;
		display: flex;
		justify-content: center;
		align-items: center;
		width: 400px;
		height: 70px;
		border: 1px solid #ffebed;
		border-radius: 30px;
		font-size: 20px;
		font-weight: bold;
		background: #fff;
		box-shadow: 3px 3px 3px 3px #e8c5c9;

	}
</style>
