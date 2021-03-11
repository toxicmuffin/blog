<template>
  <div class="h-screen flex flex-col items-center justify-center">
    <h1 class="mb-6">Categories</h1>
    <ItemList :item="categories.categories" />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  async asyncData({ $content }) {
    const categories = await $content('data/config').fetch()
    return { categories }
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
