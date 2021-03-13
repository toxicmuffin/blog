<template>
  <div class="flex flex-col items-center justify-center">
    <h1 class="mb-6">Categories</h1>
    <ItemList :item="categories.categories" class="mb-20" />
    <h2 class="text-center text-4xl mb-8">Featured Posts</h2>
    <PostList :post="featuredPosts" class="mb-16" />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  async asyncData({ $content }) {
    const categories = await $content('data/config').fetch()
    const featuredPosts = await $content('blog', { deep: true })
      .where({ tags: { $contains: 'Featured' } })
      .only(['title', 'path', 'image', 'description', 'createdAt'])
      .sortBy('createdAt', 'desc')
      .fetch()
    return { categories, featuredPosts }
  },
  head() {
    return {
      title: 'Categories | Kai Asuncion',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: '',
        },
        {
          hid: 'description',
          name: 'description',
          content: '',
        },
        // Open Graph
        { hid: 'og:title', property: 'og:title', content: '' },
        {
          hid: 'og:description',
          property: 'og:description',
          content: '',
        },
        // Twitter Card
        {
          hid: 'twitter:title',
          name: 'twitter:title',
          content: '',
        },
        {
          hid: 'twitter:description',
          name: 'twitter:description',
          content: '',
        },
      ],
    }
  },
})
</script>
