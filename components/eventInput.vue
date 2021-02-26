<template>
	<div class="input-box" :class="[inputType, styleType]" >
		<label v-if="isLabelLeft()" :for="id"><slot/></label>

		<input
			:type="inputType"
			:name="name"
			:id="id"
			:placeholder="placeholder"
			:value="value"
			:disabled='disabled'
			:readonly='readonly'
			:checked="checked"
			@input="change"
		>

		<label v-if="!isLabelLeft()" :for="id"><slot/></label>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import { Component, Prop } from "vue-property-decorator";

@Component
export default class EventInput extends Vue {

	@Prop ({default: 'text'}) inputType?:	string
	@Prop ({default: ''}) name?:			string
	@Prop ({default: ''}) id?:				string
	@Prop ({default: ''}) placeholder?: 	string
	@Prop ({default: ''}) value?:			string
	@Prop ({default: false}) disabled?:		boolean
	@Prop ({default: false}) readonly?:		boolean
	@Prop ({default: false}) checked?:		boolean
	@Prop ({default: ''}) styleType?:		string

	isLabelLeft(): boolean {
		switch (this.inputType) {
			case 'radio':
			case 'checkbox':
			case 'file':
				return false
			default:
				return true
		}
	}

	change($event: any) {
		if(this.inputType === 'checkbox') {
			this.$emit('input', $event.target.checked)
		} else if(this.inputType === 'file') {
			let files = $event.target.files || $event.dataTransfer.files
			this.$emit('input', files)
		} else {
			this.$emit('input', $event.target.value)
		}
	}
}
</script>

<style lang="scss" scoped>
@import "@/assets/scss/mixin";

.text {
	width: 100%;
	height: 60px;
	margin-bottom: 22px;
	&.line-input {
		border: 1px solid #d3d3d3;
	}

	input {
		width: 100%;
		height: 100%;
		padding: 0 25px;
		font-size: 20px;
		background-color: #f3f3f3;
		&::placeholder {
			font-size: 20px;
			font-weight: 300;
			color: $lightGray;
		}
	}
}

.file {
	display: flex;
	justify-content: center;
	align-items: center;
	width: 60px;
	height: 60px;
	border-radius: 5px;
	background-color: #bababa;
	label {
		width: 39px;
		height: 39px;
		background: url('~@/assets/images/common/ico_file.png') center no-repeat;
	}
	input {
		display: none;
	}
}

.checkbox {
	.point {
		color: #c83030;
	}

	input {
		display: none;

		&:checked {
			+ label {
				&:after {
					background-color: $red;
				}
			}
		}

		+ label {
			position: relative;
			display: block;
			padding-left: 35px;
			color: #333;
			text-align: left;

			&:before,
			&:after {
				content: '';
				display: inline-block;
				position: absolute;
				margin: auto;
			}

			&:before {
				left: 2px;
				top: 0;
				width: 19px;
				height: 15px;
				background: url('~@/assets/images/common/checkbox.png') no-repeat;
				z-index: 1;
			}

			&:after {
				top: 0;
				bottom: 0;
				left: 0;
				width: 24px;
				height: 24px;
				background-color: #e6e6e6;
			}
		}
	}
}

.m-file{ margin-right: 15px; }

.radio {
	&.age-radio {
		margin: 0 auto;

		label {
			display: inline-block;
			width: 100px;
			height: 50px;
			font-size: 20px;
			line-height: 50px;
			text-align: center;
			border: 1px solid #b3b3b3;
		}
		:checked + label {
			color: $white;
			background-color: $darkGray;
		}
	}
}
</style>
