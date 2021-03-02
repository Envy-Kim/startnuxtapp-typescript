<template>
	<div>
		가게정보
		<slot name='list' />

		<slot name='vote' />
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

.store-p {
	margin: 17px 0;
	line-height: 24px;
	font-size: 18px;
	.point {
		color: #ff5f50;
		font-weight: 500;
	}
}
</style>
