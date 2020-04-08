<template>
  <div class="container">
    <todo-header></todo-header>
  </div>
</template>

<script>
import header from '@/components/header.vue'

export default {
  components: {
    'todo-header': header
  }
}
</script>

<style lang="scss" scoped>
  .container {
    margin: 0 auto;
    width: 500px;
    background-color: rgba(255, 255, 255, 1);
    border-radius: 15px 15px 0 0;
  }
</style>