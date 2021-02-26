<template>
  <div>
	  <!--
	  header, footer 등은 구성요소(Component)에 생성,
	  layouts 디렉토리에는 바로 사용 가능한 최종 layout을 생성
	  -->
	  <nuxt />
	  <event-footer />
  </div>
</template>

<script>
import EventFooter from "~/components/eventFooter";
export default {
	components: {EventFooter}
}
</script>
