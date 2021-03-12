<template>
  <div class="footer-list-container">
    <ul class="footer-list">
      <li><NuxtLink to="/">Home</NuxtLink></li>
      <li><NuxtLink to="/categories">Categories</NuxtLink></li>
      <li><NuxtLink to="/about">About</NuxtLink></li>
    </ul>
    <span class="vertical-line"></span>
    <ul class="footer-list">
      <li>
        <NuxtLink to="/categories/front-end-development">
          Front End Development
        </NuxtLink>
      </li>
      <li><NuxtLink to="/categories/photography">Photography</NuxtLink></li>
      <li>
        <NuxtLink to="/categories/cryptocurrency">Cryptocurrency</NuxtLink>
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
.footer-list-container {
  margin: 2rem;
  display: flex;
  justify-content: center;
  width: 100%;
  max-width: 600px;
  .vertical-line {
    width: 2px;
    background: var(--border-color);
  }
  .footer-list {
    display: flex;
    flex-flow: column nowrap;
    align-items: center;
    width: 100%;
    a {
      margin: 1rem 0;
      &:hover {
        text-decoration: underline;
      }
    }
  }
}
</style>
