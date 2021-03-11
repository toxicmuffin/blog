<template>
  <div class="flex flex-col items-center justify-center text-center">
    <div>
      <h1>Error: {{ error.statusCode }}</h1>
      <h1>{{ error.message }}</h1>
      <h2 class="hover:underline text-2xl">
        <NuxtLink to="/" class="primary-color">Return Home</NuxtLink>
      </h2>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  props: {
    error: {
      type: Object,
      default: () => null,
    },
  },
})
</script>
