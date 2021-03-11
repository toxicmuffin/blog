<template>
  <footer>
    <NuxtLink to="/" class="footer-heading heading tracking-widest">
      Kai Asuncion
    </NuxtLink>
    <NuxtLink to="/about" class="footer-contact heading sub-heading">
      Contact
    </NuxtLink>
    <FooterNav />
    <DarkMode />
    <p class="copy-place-holder">Kai Asuncion 2021</p>
  </footer>
</template>

<script lang="ts">
import Vue from 'vue'
import DarkMode from './DarkMode.vue'
export default Vue.extend({
  components: { DarkMode },
})
</script>

<style lang="scss" scoped>
footer {
  position: relative;
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
  transition: background-color 0.3s;
  padding: 2rem 0;
  .footer-heading {
    font-size: 2rem;
    margin-bottom: 0.5rem;
  }
  .sub-heading {
    font-family: 'Raleway', serif;
  }
  .footer-contact {
    font-size: 1.5rem;
    margin-bottom: 0.5rem;
  }
  .footer-nav {
    display: flex;
    flex-flow: column nowrap;
    align-items: center;
  }
  .copy-place-holder {
    text-align: center;
    position: absolute;
    bottom: 0;
    color: var(--color-primary);
  }
}
</style>
