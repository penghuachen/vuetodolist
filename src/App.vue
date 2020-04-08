<template>
  <div id="app">
    <container-components />
  </div>
</template>

<script>
import container from '@/views/container.vue'

export default {
  components: {
    'container-components': container
  }
}
</script>

<style lang="scss">
  p {
    margin: 0;
  }
  svg {
    cursor: pointer;
  }
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }
  body {
    height: 100vh;
    background: rgba(0, 0, 0, 0.1);
  }
</style>
