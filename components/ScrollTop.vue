<template>
  <button class="main-button mx-auto" @click="toTop">Back to Top</button>
</template>

<script>
export default {
  methods: {
    toTop() {
      this.intervalId = setInterval(() => {
        if (window.pageYOffset === 0) {
          clearInterval(this.intervalId)
        }
        window.scroll(0, window.pageYOffset - 20)
      }, 1)
    },
  },
}
</script>
