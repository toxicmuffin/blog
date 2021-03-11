<template>
  <ul class="flex flex-wrap justify-center flex-row">
    <li
      v-for="content in item"
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
        </div>
      </NuxtLink>
    </li>
  </ul>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  props: {
    item: {
      type: Array,
      required: true,
      default: () => null,
    },
  },
})
</script>

<style scoped>
li:hover {
  box-shadow: -0.5rem 0 var(--color-primary);
  transition: ease 0.4s;
}
</style>
