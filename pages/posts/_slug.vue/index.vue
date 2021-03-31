<template>
  <div class="single-post-page">
    <section class="post">
      <h1>{{ doc.title }}</h1>
      <div class="post-details">
        <div>Last updated on {{ doc.updatedAt | formatDate }}</div>
        <div>Writen by {{ doc.author }}</div>
      </div>
      <nuxt-content :document="doc" />
      <v-row> <v-col></v-col></v-row>
      <v-row>
        <v-col>
          <v-btn v-if="prev" :to="prev.slug">Prev</v-btn>
        </v-col>
        <v-col class="d-flex justify-end">
          <v-btn v-if="next" :to="next.slug">Next</v-btn>
        </v-col>
      </v-row>
    </section>
  </div>
</template>

<script>
import { format } from 'date-fns'
export default {
  filters: {
    formatDate() {
      return format(new Date(), 'dd MMM yyyy')
    },
  },
  async asyncData({ $content, params }) {
    const doc = await $content(`blog/${params.slug}` || 'index').fetch()
    const [prev, next] = await $content('blog')
      .only(['title', 'slug'])
      .sortBy('title', 'Asc')
      .surround(params.slug, { before: 1, after: 1 })
      .fetch()
    return { doc, prev, next }
  },
}
</script>
