<template>
  <div>
    <PostHeading
      :blog-title="blogPost.title"
      :author="blogPost.author"
      :date="blogPost.createdAt"
      :image="blogPost.image"
      :ttr="blogPost.body"
    />
    <nuxt-content :document="blogPost" />
    <ScrollTop />
  </div>
</template>

<script lang="ts">
export default {
  layout: 'blogPost',
  async asyncData({ $content, params, error }) {
    const path = `/${params.pathMatch || 'index'}`
    const [blogPost] = await $content('blog', { deep: true })
      .where({ path })
      .fetch()
    if (!blogPost) {
      return error({ statusCode: 404, message: 'Page not found - ' + path })
    }
    return { blogPost }
  },
  head() {
    return {
      title: this.blogPost.title + ' | Kai Asuncion',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.blogPost.description,
        },
        {
          hid: 'description',
          name: 'description',
          content: this.blogPost.description,
        },
        // Open Graph
        { hid: 'og:title', property: 'og:title', content: this.blogPost.title },
        {
          hid: 'og:description',
          property: 'og:description',
          content: this.blogPost.description,
        },
        // Twitter Card
        {
          hid: 'twitter:title',
          name: 'twitter:title',
          content: this.blogPost.title,
        },
        {
          hid: 'twitter:description',
          name: 'twitter:description',
          content: this.blogPost.description,
        },
      ],
    }
  },
}
</script>
