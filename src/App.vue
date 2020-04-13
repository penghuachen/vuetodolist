<template>
  <div id="app">
    <div class="container">
      <todo-header :filter-list.sync="filterTodoList" />
      <todo-content 
        :filter-list="filterTodoList" 
        :statusArea="statusArea"
        @updateTaskHandler="updateTaskHandler"
        @deleteTaskHandler="deleteTaskHandler"
        @editTaskHandler="editTaskHandler"
        @updateStatusAreaHandler="updateStatusAreaHandler"
        />
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
    todoList: JSON.parse(localStorage.getItem('todos')) || [],
    statusArea: '全部'
    }
  },
  methods: {
    addTask(taskObj) {
      this.todoList.push(taskObj);
      this.storeInLocalStorage(this.todoList);
    },
    updateTaskHandler(todo) {
      const isTarget = this.todoList.find(task => task.id = todo.id);
      if(!isTarget) return;

      todo.done = !todo.done;
      const index = this.todoList.indexOf(todo);
      this.todoList.splice(index, 1, todo);
      this.storeInLocalStorage(this.todoList);;
    },
    deleteTaskHandler(index) {
      this.todoList.splice(index, 1);
      this.storeInLocalStorage(this.todoList);
    },
    editTaskHandler(index, newTaskContent) {
      this.todoList[index].edit = !this.todoList[index].edit;
      this.todoList[index].task = newTaskContent;
      this.storeInLocalStorage(this.todoList);
    },
    updateStatusAreaHandler(area) {
      this.statusArea = area;
    },
    storeInLocalStorage(data) {
      localStorage.setItem('todos', JSON.stringify(data));
    }
  },
  computed: {
    filterTodoList() {
      const obj = {
        '全部': this.todoList,
        '進行中': this.todoList.filter(task => !task.done),
        '已完成': this.todoList.filter(task => task.done)
      };
      return obj[this.statusArea];
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
