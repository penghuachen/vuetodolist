<template>
  <div class="task-list">
    <div class="task" 
      v-for="(todo, index) in todoList" 
      :key="index"
      :id="todo.id"
      >
        <div class="undone"
          v-if="!todo.done"
          @click="emitUpdateHandler(index)"
          >
        </div>
        <div class="done"
          v-if="todo.done" 
          @click="emitUpdateHandler(index)"
          >
          <checkIcon />
        </div>
        <div class="task-content" 
          :class="{ 'line-through': todo.done }">
          <p v-if="!todo.edit">{{ todo.task }}</p>
          <input 
            class="editTask"
            type="text"
            v-if="todo.edit"
            :value="todo.task"
          >
        </div>
        <div class="delete-icon">
          <deleteIcon />
        </div> 
    </div>
  </div>
</template>

<script>
import checkIcon from '@/assets/img/check-icon.svg';
import deleteIcon from '@/assets/img/delete-icon.svg';

export default {
  props: {
    todoList: {
      type: Array
    }
  }, 
  methods: {
    emitUpdateHandler(index) {
      this.$emit('updateTaskHandler', index);
    },
  },
  components: {
    checkIcon,
    deleteIcon
  }
}
</script>

<style lang="scss">
  .task-list {
    overflow: auto;
    height: 350px;
  }
  .task {
    display: flex;
    align-items: center;
    border-bottom: 1px solid rgba(0,0,0,0.1);
    padding: 16px 10px;
  }
  .undone, .done {
    cursor: pointer;
    flex: 1 0 auto;
    width: 20px;
    height: 20px;
    border-radius: 999px;
  }
  .undone {
    border: 2px solid #000;
  }
  .done {
    background-color: rgba(110, 178, 0, 1); 
    border: 2px solid rgba(110, 178, 0, 1);;
    text-align: center;
    svg {
      width: 15px;
      height: 15px;
      line-height: 20px;
    }
  }
  .task-content {
    width: 470px;
    padding: 0 10px;
    .editTask {
      width: 92%;
      height: 20px;
      border-radius: 5px;
      border: 1px solid #bdbd;
      outline: none;
      font-size: 18px;
      padding: 5px 10px;
    }
  }
  .line-through {
    text-decoration: line-through;
    color: rgba(0,0,0,0.1);
  }
  .delete-icon {
    width: 20px;
    svg {
      vertical-align: bottom;
      transition: fill .2s;
      &:hover {
        fill: #f00;
      }
    }
  }
</style>