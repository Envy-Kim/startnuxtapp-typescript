<template>
	<div :style="{'left':left, 'bottom':bottom}">
		<div v-if="btnType === 'default'">
			<button >default</button>
		</div>

		<div v-else-if="btnType === 'detail-btn' || btnType === 'line-type'"
			 :class="[btnType, { 'on': (btnType === 'detail-btn' && on) }]">
			<nuxt-link
				:class="colorType"
				:style="{'width' : width}"
				to="">
				<p><slot/></p>
			</nuxt-link>
		</div>

		<nuxt-link v-else
			:class="btnType"
			:style="{'width' : width, 'height' : height}"
			to="">
			<p><slot/></p>
		</nuxt-link>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import Component from "vue-class-component";
import { Prop } from 'vue-property-decorator'

@Component
export default class Btn extends Vue {
	@Prop({default: 'default'}) btnType?: string
	@Prop({default: 'light-gray'}) colorType?: string
	@Prop({default: '100px'}) width?: string
	@Prop({default: '54px'}) height?: string
	@Prop({default: ''}) funcType?: string
	@Prop({default: '0'}) left?: string
	@Prop({default: '0'}) bottom?: string
	@Prop({default: false}) on?: boolean
}
</script>

<style lang='scss' scoped>
@import "@/assets/scss/mixin";

.btn-box {
	position: absolute;
	bottom: 0;
}
.line-type {
	a {
		height: 30px;
		display: flex;
		justify-content: center;
		align-items: center;
		border-radius: 30px;
		p {
			position: relative;
			display: inline-block;
			padding-right: 10px;
			&::after {
				content: '';
				display: block;
				position: absolute;
				right: 0;
				top: 1px;
				bottom: 0;
				margin: auto;
				width: 8px;
				height: 8px;
				transform: rotate(45deg);
			}
		}
		&.color-yellow {
			border: 1px solid #fff;
			p {
				color: white;
				&::after {
					border-top: 2px solid $yellow;
					border-right: 2px solid $yellow;
				}
			}
		}
		&.color-pink {
			border: 1px solid #959090;
			p {
				color: #342c2b;
				&::after {
					border-top: 2px solid $pink;
					border-right: 2px solid $pink;
				}
			}
		}
		&.color-pink-white {
			border: 1px solid #959090;
			p {
				color: white;
				&::after {
					border-top: 2px solid $pink;
					border-right: 2px solid $pink;
				}
			}
		}
		&:hover {
			&.color-pink {
				background-color: #e4584b;
				p {
					color: white;
					&::after {
						border-top: 2px solid $white;
						border-right: 2px solid $white;
					}
				}
			}
		}

	}
}

.detail-btn {
	&.on {
		a {
			p {
				&::after {
					top: 3px;
					border-left: 2px solid #666;
					border-top: 2px solid #666;
					border-bottom: 0;
					border-right: 0;
				}
			}
		}
	}
	a {
		width: 100px;
		height: 24px;
		display: flex;
		justify-content: center;
		align-items: center;
		border: 1px solid $lightGray;
		border-radius: 15px;
		p {
			position: relative;
			display: inline-block;
			padding-right: 15px;
			font-size: 14px;
			color: #666;
			&::after {
				content: '';
				display: block;
				position: absolute;
				right: 0;
				bottom: 0;
				margin: auto;
				width: 8px;
				height: 8px;
				top: -3px;
				border-left: 0;
				border-top: 0;
				border-bottom: 2px solid #666;
				border-right: 2px solid #666;
				transform: rotate(45deg);
			}
		}
	}
}

.bg-type {
	a {
		display: flex;
		justify-content: center;
		align-items: center;
		border-radius: 30px;
		p {
			font-size: 24px;
			color: $white;
		}
		&.btn-cancel {
			background-color: $lightGray;
		}
		&.btn-confirm {
			background-color: $darkGray;
		}
		&.btn-entry {
			font-family: 'BMJUA';
			box-shadow: 5px 5px 1px rgba(0,0,0,.1);
			background-color: #fffa6f;
			p {
				position: relative;
				padding-right: 25px;
				font-size: 34px;
				color: #483d37;
				&::after {
					content: '';
					display: block;
					position: absolute;
					right: 0;
					top: -3px;
					bottom: 0;
					margin: auto;
					width: 16px;
					height: 26px;
					background: url('~@/assets/images/tab01/btn_entry_arrow.png');
				}
			}
		}
		&.btn-more {
			box-shadow: 5px 5px 1px rgba(0,0,0,.1);
			background-color: $white;
			p {
				position: relative;
				padding-left: 34px;
				font-size: 22px;
				font-weight: 700;
				color: #3e2e2f;
				&::before {
					content: '';
					display: block;
					position: absolute;
					left: 0;
					top: 0;
					bottom: 0;
					margin: auto;
					width: 23px;
					height: 23px;
					background: url('~@/assets/images/common/ico_add.png');
				}
			}
		}
		&.btn-vote {
			border-radius: 5px;
			background-color: #ff887d;
			p {
				position: relative;
				font-size: 20px;
				padding-left: 33px;
				&::before {
					content: '';
					display: block;
					position: absolute;
					left: 0;
					top: 0;
					bottom: 0;
					margin: auto;
					width: 27px;
					height: 26px;
					background: url('~@/assets/images/common/ico_heart.png');
				}
			}
		}
	}
}
</style>
