<template>
	<div class="ev-section" :class="secClass" >
		<img v-if="src != 'none'" :src="src" alt="" />
		<slot></slot>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import {Component, Prop} from "vue-property-decorator";

@Component
export default class EventSection extends Vue {
	@Prop({default: ''}) src?: string
	@Prop({default: ''}) secClass?: string
}
</script>

<style lang="scss">

.ico-banner {
	position: absolute;
	bottom: 0;
	left: 230px;
}

.ev-section {
	position: relative;
}

.ev2-bg-color {
	background-color: #ffeaec;
}

.modal-head {
	.point {
		color: #c83030;
	}
}

.modal-subtit {
	.point {
		margin-top: 6px;
		margin-bottom: 30px;
		display: block;
		font-size: 18px;
		color: #c86930;
		line-height: 24px;
	}
}

.select {
	display: flex;
	justify-content: space-between;
	align-items: flex-end;
	margin-top: 30px;
	li {
		overflow: hidden;
		cursor: pointer;
		text-indent: -9999px;
		&:hover {
			&:nth-child(1) {
				background-position: 0 0;
			}
			&:nth-child(2) {
				background-position: 0 0;
			}
		}
		&:nth-child(1) {
			width: 280px;
			height: 365px;
			background: url('~@/assets/images/tab01/popup_select01.png') no-repeat;
			background-position: -280px 0;
		}
		&:nth-child(2) {
			width: 264px;
			height: 340px;
			background: url('~@/assets/images/tab01/popup_select02.png') no-repeat;
			background-position: -264px 0;
		}
	}
}

.flex-box {
	display: flex;
	align-items: center;
}

.input-area {
	margin-bottom: 12px;
	.flex-box {
		.bg-type {
			margin-left: 8px;
		}
		.input-box {
			margin-bottom: 0;
		}
	}
	.info {
		display: block;
		margin-top: 8px;
		margin-left: 20px;
		text-align: left;
		color: #999;
		font-weight: 300;
	}
}

.confirm-btn {
	margin-top: 30px;
}

.bg-type {
	display: flex;
	justify-content: center;
}
</style>
