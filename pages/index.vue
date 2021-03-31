<template>
  <div class="home-page">
    <section class="intro">
      <h1>Get the latest News!</h1>
    </section>
    <section class="featured-posts">
      <PostsList :posts="docs" />
    </section>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const docs = await $content(`blog`).sortBy('title').fetch()
    return { docs }
  },
  data() {
    return {
      posts: [],
    }
  },
}
</script>
