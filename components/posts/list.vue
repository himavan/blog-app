<template>
  <v-row>
    <v-col v-for="p in allPosts" :key="p.id" cols="3">
      <PostPreviewCard
        :id="p.slug"
        :title="p.title"
        :thumbnail="p.thumbnail"
        :post-link="p.path"
        :date="p.createdAt | formatDate"
        :exert="p.exerpt"
        :author="p.author"
      />
    </v-col>
  </v-row>
</template>
<script>
import PostPreviewCard from '@/components/posts/preview-card'
import { format } from 'date-fns'
export default {
  components: {
    PostPreviewCard,
  },
  filters: {
    formatDate() {
      return format(new Date(), 'dd MMM yyyy')
    },
  },
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      allPosts: this.posts ? [...this.posts] : [],
    }
  },
}
</script>
<style scoped></style>
