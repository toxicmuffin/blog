<template>
  <nav :class="{ 'navbar--hidden': !showNavBar }">
    <NuxtLink class="brand-logo" aria-label="Logo - Home link" to="/">
      <Logo />
    </NuxtLink>
    <button
      aria-label="menu button"
      class="hamburger-icon"
      :class="menuOpen ? 'mustard' : ''"
      @click="isMenuOpen()"
    >
      <span class="top-bun"></span>
      <span class="patty"></span>
      <span class="bottom-bun"></span>
    </button>
    <ul
      :class="menuOpen ? 'hamburger-open' : 'hamburger-closed'"
      class="nav-menu"
    >
      <li @click="closeBurger()">
        <NuxtLink to="/" class="nav-item">Home</NuxtLink>
      </li>
      <li @click="closeBurger()">
        <NuxtLink to="/categories" class="nav-item">Categories</NuxtLink>
      </li>
      <li @click="closeBurger()">
        <NuxtLink to="/about" class="nav-item">About</NuxtLink>
      </li>
    </ul>
  </nav>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  data() {
    return {
      menuOpen: false,
      showNavBar: true,
      lastScrollPosition: 0,
    }
  },
  mounted() {
    document.addEventListener('click', this.closeMenu)
    window.addEventListener('scroll', this.onScroll)
  },
  beforeDestroy() {
    document.addEventListener('click', this.closeMenu)
    window.removeEventListener('scroll', this.onScroll)
  },
  methods: {
    closeMenu(e: any) {
      if (!this.$el.contains(e.target) && this.menuOpen === true) {
        this.menuOpen = false
        document.body.style.overflow = 'auto'
      }
    },
    isMenuOpen() {
      if (!this.menuOpen) {
        this.menuOpen = true
        document.body.style.overflow = 'hidden'
      } else {
        this.menuOpen = false
        document.body.style.overflow = 'auto'
      }
    },
    closeBurger() {
      this.menuOpen = false
      document.body.style.overflow = 'auto'
    },
    onScroll() {
      const currentScrollPosition: number =
        window.pageYOffset || document.documentElement.scrollTop
      if (currentScrollPosition < 0) {
        return
      }
      if (Math.abs(currentScrollPosition - this.lastScrollPosition) < 100) {
        return
      }
      this.showNavBar = currentScrollPosition < this.lastScrollPosition
      this.lastScrollPosition = currentScrollPosition
    },
  },
})
</script>

<style lang="scss" scoped>
$xtra_small: 'max-width: 639px';
$small: 'min-width: 640px';
@mixin xtra_small {
  @media only screen and ($xtra_small) {
    @content;
  }
}
@mixin small {
  @media only screen and ($small) {
    @content;
  }
}
nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 4rem;
  padding: 0.5rem;
  background-color: var(--bg);
  width: 100%;
  position: fixed;
  transition: 0.4s ease-out;
  z-index: 1;
  &.navbar--hidden {
    transform: translateY(-120%);
  }
  @include small {
    align-items: end;
    .nav-cart {
      order: 3;
    }
  }
  .brand-logo {
    height: 100%;
  }
  .hamburger-icon {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 48px;
    width: 48px;
    z-index: 2;
    @include small {
      display: none;
    }
    .patty,
    .top-bun,
    .bottom-bun {
      content: '';
      background-color: var(--color);
      position: absolute;
      width: 48px;
      height: 0.25rem;
      transition: all 0.5s ease-in-out;
      z-index: 2;
    }
    .top-bun {
      transform: translateY(-16px);
    }
    .bottom-bun {
      transform: translateY(16px);
    }
    &.mustard {
      .top-bun {
        transform: rotate(45deg);
      }
      .bottom-bun {
        transform: rotate(-45deg);
      }
      .patty {
        transform: translateX(-50px);
        background-color: transparent;
      }
    }
  }
  .nav-menu {
    background-color: var(--bg);
    z-index: 1;
    display: flex;
    transition: ease-in-out 0.4s;
    @include xtra_small {
      flex-flow: column nowrap;
      width: 100%;
      top: 0;
      right: -120%;
      height: 100vh;
      position: fixed;
      max-width: 500px;
      box-shadow: 0 0 2rem var(--shadow-color);
      align-items: start;
      justify-content: space-evenly;
      li {
        margin-left: 2rem;
      }
      .nav-item {
        width: 100%;
        font-size: 1.5rem;
        padding: 1rem 2rem;
        &:hover {
          box-shadow: -5px 0 var(--border-color);
        }
      }
    }
    @include small {
      flex-flow: row wrap;
      justify-content: space-evenly;
      position: relative;
      order: 2;
      .nav-item {
        margin: 0 0.5rem;
        padding: 0 0.5rem;
        &:hover {
          box-shadow: -5px 0 var(--border-color);
        }
      }
    }
    .nuxt-link-exact-active {
      // font-weight: bold;
      box-shadow: -5px 0 var(--button-color);
    }
    .nav-item {
      transition: 0.2s ease-out;
    }
  }
  .hamburger-open {
    right: 0;
  }
}
</style>
