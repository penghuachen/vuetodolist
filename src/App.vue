<template>
  <div id="app">
    <div class="container">
      <todo-header :todo-list.sync="todoList" />
      <todo-content :todo-list="todoList" />
      <todo-addtask @addTask="addTask" /> 
    </div>
  </div>
</template>

<script>
import header from '@/components/header.vue';
import content from '@/components/content.vue';
import addTask from '@/components/add-task.vue';

export default {
  data() {
    return {
    todoList: []
    }
  },
  methods: {
    addTask(taskObj) {
      this.todoList.push(taskObj);
    }
  },
  components: {
    'todo-header': header,
    'todo-content': content,
    'todo-addtask': addTask
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
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
  }
  body {
    height: 100vh;
    background: rgba(0, 0, 0, 0.1);
  }
  .container {
    margin: 0 auto;
    width: 500px;
    background-color: rgba(255, 255, 255, 1);
    border-radius: 15px 15px 0 0;
  }
</style>
