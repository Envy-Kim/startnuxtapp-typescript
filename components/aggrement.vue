<template>
	<div class="agreement">
		<div
			:class="{'on' : isShow}"
			class="checkbox-area">
			<slot name='checkbox'/>
			<btn
				:style="{'padding-left':paddingLeft}"
				btn-type='detail-btn'
				colorType='light-gray'
				width='100'
				:on="isShow"
				@click.native="isShow = !isShow" >
				<slot name='detail_btn_text' />
			</btn>
		</div>

		<transition name="slide-down">
			<div
				v-if="isShow"
				class="agreement-content">
				<div class="wrap">
					<slot name='content'/>
				</div>
			</div>
		</transition>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue'
import { Component, Prop, Watch } from 'vue-property-decorator'

@Component
export default class Aggrement extends Vue {
	@Prop({default: ''}) name ?: string
	@Prop({default: ''}) id ?: string
	@Prop({default: ''}) value ?: string
	@Prop({default: '20px'}) paddingLeft ?: string

	isShow: boolean = false

}
</script>

<style lang='scss' scoped>

@import "@/assets/scss/mixin";

.agreement {
	margin-bottom: 15px;
}

.checkbox-area {
	display: flex;
	align-items: center;
	&.on {
		margin-bottom: 15px;
	}
	.check-box {
		width: 235px;
	}
}

.agreement-content {
	width: 100%;
	height: 120px;
	background-color: #f3f3f3;
	overflow-y: scroll;
	.wrap {
		padding: 20px;
		line-height: 25px;
		text-align: left;
		color: #666;
	}
}

.slide-down-enter-active {
	transition: all .5s ease;
}

.slide-down-enter, .slide-down-leave-to {
	height: 0;
	opacity: 0;
	transition: all .5s ease;
}
</style>
