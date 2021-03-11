<template>
  <div>
    <PostList :post="posts" />
    {{ category }}
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  async asyncData({ $content, params, error }) {
    const CatPath = params.categories
    const posts = await $content('blog', CatPath, { deep: true })
      .without('body')
      .fetch()
      .catch(() => {
        error({ statusCode: 404, message: 'Page not found' })
      })
    return { posts }
  },
})
</script>

<style scoped>
h1 {
  text-align: center;
  padding: 1rem;
  margin-bottom: 1rem;
  box-shadow: 0 0.25rem var(--border-color);
}
</style>
