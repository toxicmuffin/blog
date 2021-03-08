<template>
  <div class="w-10/12 m-auto max-w-screen-md">
    <nuxt-content :document="blogPost" />
  </div>
</template>

<script lang="ts">
export default {
  async asyncData({ $content, params, error }) {
    const path = `/${params.pathMatch || 'index'}`
    console.log(path)
    const [blogPost] = await $content('blog', { deep: true })
      .where({ path })
      .fetch()
    if (!blogPost) {
      return error({ statusCode: 404, message: 'Page not found - ' + path })
    }
    return { blogPost }
  },
}
</script>
