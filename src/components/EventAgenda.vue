<template>
<div>
  {{this.$route.params.organizerSlug}}
  {{this.$route.params.eventSlug}}
</div>
</template>

<script>
export default {
  name: "EventAgenda"
}
</script>

<style scoped>

</style>