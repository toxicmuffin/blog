<template>
  <div class="rainbow-container">
    <div class="rainbow-wrapper">
      <div class="rainbow blue"></div>
      <div class="rainbow green"></div>
      <div class="rainbow yellow"></div>
      <div class="rainbow red"></div>
      <div class="rainbow pink"></div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.rainbow-container {
  position: relative;
  height: 3rem;
  @screen md {
    height: 6rem;
  }
}
.rainbow-wrapper {
  z-index: -1;
  width: 200vw;
  margin: auto;
  position: absolute;
  left: -100px;
}
.rainbow {
  width: 100%;
  height: 0.5rem;
  margin-bottom: 0.25rem;
  @screen md {
    height: 1rem;
  }
  &.blue {
    background-color: #0099cb;
  }
  &.green {
    background-color: #690;
  }
  &.yellow {
    background-color: #fc0;
  }
  &.red {
    background-color: #f30;
  }
  &.pink {
    background-color: #f36;
  }
}
</style>
