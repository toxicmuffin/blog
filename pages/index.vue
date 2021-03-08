<template>
  <div class="splash-container">
    <div class="w-full transform lg:-rotate-12">
      <h1>Hello,</h1>
      <h1>Welcome To My&nbsp;Blog</h1>
      <Rainbow class="mb-2" />
      <ul class="flex flex-wrap justify-center list-disc">
        <li v-for="topics in categories.category" :key="topics.title">
          <h2>
            <NuxtLink :to="`categories/${topics.path}`">{{
              topics.title
            }}</NuxtLink>
          </h2>
        </li>
      </ul>
    </div>
    <ul>
      <li v-for="topics in categories.category" :key="topics.title">
        {{ topics.title }}
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  async asyncData({ $content }) {
    const categories = await $content('data/config').fetch()
    return { categories }
  },
})
</script>

<style lang="scss" scoped>
@import url('~/assets/styles/variables/colors.scss');
.splash-container {
  min-height: 100vh;
  width: 100%;
  display: flex;
  flex-flow: column nowrap;
  justify-content: center;
  text-align: center;
  overflow: hidden;
  letter-spacing: 0.35rem;
}
li {
  @apply ml-6;
  h2 {
    font-family: var(--secondary-font);
  }
}
</style>
