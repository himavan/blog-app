<template>
  <div class="home-page">
    <section class="intro">
      <v-row>
        <v-col>
          <h1>All Posts!</h1>
        </v-col>
      </v-row>
    </section>
    <section class="featured-posts">
      <PostsList :posts="doc" />
    </section>
  </div>
</template>

<script>
export default {
  async asyncData({ $content }) {
    const doc = await $content(`blog`).sortBy('title').fetch()
    return { doc }
  },
  data() {
    return {
      posts: [],
    }
  },
}
</script>
