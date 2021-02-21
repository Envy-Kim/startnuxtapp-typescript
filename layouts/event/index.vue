<template>
  <div>
	  <nuxt />
	  <event-footer />
  </div>
</template>

<script>
import EventFooter from "~/layouts/event/eventFooter";
export default {
	components: {EventFooter}
}
</script>
