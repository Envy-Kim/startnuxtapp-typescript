<template>
	<div>
		가게정보
		<slot name='list' />

		<div class='input-area'>
			<div class='flex-box'>
				<slot name='vote' />
			</div>
		</div>
	</div>
</template>

<script lang='ts'>
import Vue from 'vue'
import { Component } from 'vue-property-decorator'

@Component
export default class StoreInfo extends Vue {
}
</script>

<style lang='scss' scoped>
.input-area {
	margin-bottom: 12px;

	.flex-box {
		display: flex;
		align-items: center;
		justify-content: center;
	}
}
</style>
