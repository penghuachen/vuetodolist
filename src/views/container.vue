<template>
  <div class="container">
    <todo-header></todo-header>
    <todo-content></todo-content>
    <todo-addtask></todo-addtask>
  </div>
</template>

<script>
import header from '@/components/header.vue';
import content from '@/components/content.vue';
import addTask from '@/components/add-task.vue';

export default {
  components: {
    'todo-header': header,
    'todo-content': content,
    'todo-addtask': addTask,
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