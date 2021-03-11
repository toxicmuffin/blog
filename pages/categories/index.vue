<template>
  <div class="splash-container">
    <ul>
      <li v-for="topics in categories.categories" :key="topics.title">
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
}
li {
  @apply ml-6;
  h2 {
    font-family: var(--secondary-font);
  }
}
</style>
