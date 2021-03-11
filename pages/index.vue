<template>
  <div>
    <div class="splash-container">
      <div class="w-full mb-6 transform lg:-rotate-12 lg:mb-20">
        <h1>Hello,</h1>
        <h1>Welcome To My&nbsp;Blog</h1>
        <Rainbow class="mb-2" />
        <ul class="flex flex-wrap justify-center list-disc">
          <li
            v-for="topics in categories.category"
            :key="topics.title"
            class="ml-6"
          >
            <h2>
              <NuxtLink :to="`categories/${topics.path}`">{{
                topics.title
              }}</NuxtLink>
            </h2>
          </li>
        </ul>
      </div>
    </div>
    <h2 class="text-center text-4xl mb-8">New Posts</h2>
    <PostList :post="posts" class="mb-16" />
    <h2 class="text-center text-4xl mb-8">Categories</h2>
    <ItemList :item="categories.categories" class="mb-16" />
    <h2 class="text-center text-4xl mb-8">Featured Posts</h2>
    <PostList :post="featuredPosts" class="mb-16" />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  async asyncData({ $content }) {
    const categories = await $content('data/config').fetch()
    const posts = await $content('blog', { deep: true })
      .only(['title', 'path', 'image', 'description', 'createdAt'])
      .limit(4)
      .sortBy('createdAt', 'desc')
      .fetch()
    const featuredPosts = await $content('blog', { deep: true })
      .where({ tags: { $contains: 'Featured' } })
      .only(['title', 'path', 'image', 'description', 'createdAt'])
      .limit(8)
      .fetch()
    return { categories, posts, featuredPosts }
  },
})
</script>

<style lang="scss" scoped>
@import url('~/assets/styles/variables/colors.scss');
.splash-container {
  min-height: 90vh;
  width: 100%;
  display: flex;
  flex-flow: column nowrap;
  justify-content: center;
  text-align: center;
  overflow: hidden;
  letter-spacing: 0.35rem;
}
li {
  h2 {
    font-family: var(--secondary-font);
  }
}
</style>
