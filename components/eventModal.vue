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
				<div
					class="modal-content"
					:class="padding">
					<p class="modal-subtit"><slot name="sub-title"/></p>
					<slot name="content" />
				</div>

			</div>
		</div>
	</transition>
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
