<template>
  <ul class="flex flex-wrap justify-center flex-row">
    <li
      v-for="content in post"
      :key="content.title"
      class="lg:flex items-center mx-3 mb-6 w-10/12 lg:w-5/12 p-4 cursor-pointer"
    >
      <NuxtLink :to="content.path">
        <p class="text-5xl text-center md:text-left md:mr-6">
          {{ content.image }}
        </p>
        <div>
          <h2 class="text-2xl font-bold">{{ content.title }}</h2>
          <p>{{ content.description }}</p>
          <p class="text-xs">{{ formatDate(content.createdAt) }}</p>
        </div>
      </NuxtLink>
    </li>
  </ul>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  props: {
    post: {
      type: Array,
      required: true,
      default: () => null,
    },
  },
  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('en', options)
    }
  }
})
</script>

<style scoped>
li:hover {
  box-shadow: -0.5rem 0 var(--color-primary);
  transition: ease 0.4s;
}
</style>
