<template>
  <div>
    <h1 class="tracking-wider">{{ blogTitle }}</h1>
    <p>{{ author }}</p>
    <p class="text-xs">~{{ time }} minutes</p>
    <p class="text-xs">{{ formatDate(date) }}</p>
    <p class="blog-post-image text-center">{{ image }}</p>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  props: {
    author: {
      type: String,
      default: () => null,
    },
    blogTitle: {
      type: String,
      default: () => null,
    },
    date: {
      type: String,
      default: () => null,
    },
    image: {
      type: String,
      default: () => null,
    },
    ttr: {
      type: Object,
      default: () => null,
    },
  },
  data() {
    return {
      time: 0,
    }
  },
  mounted() {
    this.readingTime()
  },
  methods: {
    readingTime() {
      const text: string = JSON.stringify(this.ttr)
      const wpm: number = 200
      const words: number = text.trim().split(/\s+/).length
      this.time = Math.ceil(words / wpm)
    },
    formatDate(date: string) {
      const options: object = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('en', options)
    },
  },
})
</script>

<style scoped>
.blog-post-image {
  font-size: 15rem;
}
</style>
