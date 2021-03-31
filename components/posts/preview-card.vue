<template>
  <v-card :id="id" class="mx-auto" max-width="400">
    <v-img class="white--text align-end" height="200px" :src="thumbnail">
      <v-card-title>{{ title }}</v-card-title>
    </v-img>

    <v-card-subtitle class="pb-0"
      >Posted on
      <span :style="{ color: $vuetify.theme.themes.dark.secondary }">{{
        date
      }}</span>
      by
      <span :style="{ color: $vuetify.theme.themes.dark.secondary }">{{
        author
      }}</span>
    </v-card-subtitle>

    <v-card-text class="text--primary">
      <div>
        <p>{{ exert }}</p>
      </div>
    </v-card-text>

    <v-card-actions>
      <v-btn color="primary" text> Share </v-btn>

      <v-btn color="orange" :to="postLink" text> Explore </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  name: 'PostPreviewCard',
  props: {
    id: {
      type: String,
      required: true,
    },
    author: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    date: {
      type: String,
      required: true,
    },
    exert: {
      type: String,
      required: true,
    },
    postLink: {
      type: String,
      required: true,
    },
    thumbnail: {
      type: String,
      required: true,
    },
  },
  data: () => ({}),
}
</script>

<style scoped>
.textColor {
  color: var(--secondary-color);
}
</style>
