<template>
	<!--
	vue transition
	최초 랜더링시 트랜지션을 적용하려면 appear 속성 추가
	-->
	<transition name="modal" appear>
		<div
			class="modal"
			@click.self="$emit('close')"
			:style="{ 'background': dimColor }">
			<div
				:class="colorType"
				class="modal-box">

				<div class="modal-head">
					<p><slot name="title" /></p>
					<nuxt-link @click.native="$emit('close')" to="">닫기</nuxt-link>
				</div>
				<div class="modal-content" :class="padding">
					<p class="modal-subtit"><slot name="sub-title" /></p>
					<slot name="content" />
				</div>
			</div>
		</div>
	</transition>
</template>

<script lang='ts'>
import Vue from 'vue';
import {Component, Prop} from "vue-property-decorator";

@Component
export default class EventModal extends Vue{
	@Prop ({default: 'modal-yellow'}) colorType?:		string
	@Prop ({default: 'pd40'}) padding?:					string

	dimColor: string = 'rgb(0,0,0,0.5)'

}
</script>

<style lang='scss' scoped>

@import "@/assets/scss/mixin";

.modal {
	position: fixed;
	display: -webkit-box;
	display: flex;
	-webkit-box-pack: center;
	justify-content: center;
	-webkit-box-align: center;
	align-items: center;
	z-index: 101;
	top: 0;
	left: 0;
	right: 0;
	bottom: 0;
	width: 100%;
	height: 100%;
	background: rgba(0, 0, 0, .5);
	z-index: 99999;

	.modal-box {
		position: relative;
		width: 640px;
		z-index: 9999;

		&.modal-pink {
			.modal-head {
				background-color: #ffdfdf;
				p {
					font-size: 36px;
					.point {
						color: #e15042;
					}
				}
			}
		}

		.modal-head {
			position: relative;
			height: 90px;
			display: flex;
			justify-content: center;
			align-items: center;
			border-radius: 30px 30px 0 0;
			background-color: #ffe362;
			p {
				font-size: 42px;
				font-family: 'BMJUA';
				.point {
					color: #c83030;
				}
			}

			a {
				position: absolute;
				width: 30px;
				height: 30px;
				top: 0;
				bottom: 0;
				right: 30px;
				margin: auto;
				background: url('~@/assets/images/common/popup_close.png') no-repeat;
				text-indent: -9999px;
			}
		}
		.modal-content {
			padding-top: 35px;
			padding-bottom: 50px;
			background-color: $white;
			border-radius: 0 0 30px 30px;
			&.pd40 {
				padding-left: 40px;
				padding-right: 40px;
			}
			&.pd50 {
				padding-left: 50px;
				padding-right: 50px;
			}
			p {
				text-align: center;
				font-size: 22px;
				font-weight: 500;
				line-height: 30px;
			}
		}
	}
}

.modal-enter-active, .modal-leave-active {
	transition: opacity 0.5s;
	.modal-box {
		transition: opacity 0.5s, transform 0.5s;
	}
}

.modal-leave-active {
	transition: opacity 0.5s ease;
}

.modal-enter, .modal-leave-to {
	opacity: 0;

	.modal-box {
		opacity: 0;
		transform: translateY(-30px);
	}
}
</style>
