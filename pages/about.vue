<template>
  <div class="about-page">
    <nuxt-content :document="doc" />
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const doc = await $content(`pages/about`).fetch()
    return { doc }
  },
}
</script>

<style scoped>
.about-page {
  text-align: center;
  padding: 30px;
}
</style>
