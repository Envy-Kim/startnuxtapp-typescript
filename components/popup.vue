<template>
	<!--
	vue transition
	최초 랜더링시 트랜지션을 적용하려면 appear 속성 추가
	-->
	<transition name="modal" appear>

	</transition>
	<div>
		popup
	</div>
</template>

<script lang='ts'>
import Vue from 'vue';
import Component from "vue-class-component";

@Component
export default class popup extends Vue{

}
</script>

<style lang='scss' scoped>

</style>
