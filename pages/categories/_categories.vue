<template>
  <div>
    {{ category }}
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  async asyncData({ $content, params }) {
    const CatPath = params.categories
    const category = await $content('blog', CatPath, { deep: true })
      .without('body')
      .fetch()

    return { category }
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
