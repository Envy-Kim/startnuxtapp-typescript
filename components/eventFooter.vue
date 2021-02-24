<template>
	<footer class="footer">
		<div class="wrap">
			<p>이벤트 유의사항</p>
			<ul>
				<li>- 경품은 실물과 다를 수 있으며, 이벤트 사정에 따라 변경될 수 있습니다.</li>
				<li>- 경품 지급을 위해 개인정보가 수집되며, 정확하지 않은 개인정보로 인한 불이익은 본인 책임입니다.</li>
				<li>- 불법적인 경로 또는 비정상적인 참여 시 당첨에서 제외되며, 당첨자 발표 이후 당첨이 취소될 수 있습니다</li>
			</ul>
		</div>
	</footer>
</template>

<script lang='ts'>
import Vue from 'vue'
import {Component} from 'vue-property-decorator'

@Component
export default class EventFooter extends Vue {
}
</script>

<style lang="scss" scoped>
@import "@/assets/scss/mixin";

.footer {
	background-color: #f3f3f3;
	.wrap {
		width: 646px;
		margin: 0 auto;
		padding: 50px 0;
		p {
			margin-bottom: 25px;
			font-size: 20px;
			color: #312928;
			font-weight: 700;
		}
		ul {
			li {
				font-size: 15px;
				color: #808080;
				line-height: 28px;
			}
		}
	}
}

</style>
