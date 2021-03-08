<template>
  <div class="error-container">
    <div>
      <h1 class="text-3xl">Error: {{ error.statusCode }}</h1>
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

<style lang="scss" scoped>
.error-container {
  display: grid;
  align-items: center;
  text-align: center;
  font-size: 1.5rem;
}
</style>
