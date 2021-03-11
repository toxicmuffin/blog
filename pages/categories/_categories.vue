<template>
  <div>
    <h1 class="mb-4 p-4 text-center">{{ CatPath }}</h1>
    <PostList :post="posts" />
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
    return { posts, CatPath }
  },
})
</script>

<style scoped>
h1 {
  text-align: center;
}
</style>
