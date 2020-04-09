<template>
  <div class="task-list">
    <div class="task" 
      v-for="(todo, index) in filterList" 
      :key="index"
      :id="todo.id"
      >
        <div class="undone"
          v-if="!todo.done"
          @click="emitUpdateHandler(todo)"
          >
        </div>
        <div class="done"
          v-if="todo.done" 
          @click="emitUpdateHandler(todo)"
          >
          <checkIcon />
        </div>
        <div class="task-content" 
          :class="{ 'line-through': todo.done }">
          <p 
            v-if="!todo.edit"
            @dblclick="emitEditHandler(index , todo.task)"
            >{{ todo.task }}</p>
          <input 
            class="editTask"
            type="text"
            v-if="todo.edit"
            :value="todo.task"
            @input="value = $event.target.value"
            @blur="!useKeyboardEvent && emitEditHandler(index, value)"
            @keydown.enter="emitEditHandler(index, value)"
          >
        </div>
        <div class="delete-icon">
          <deleteIcon @click="emitDeleteHandler(index)"/>
        </div> 
    </div>
  </div>
</template>

<script>
import checkIcon from '@/assets/img/check-icon.svg';
import deleteIcon from '@/assets/img/delete-icon.svg';

export default {
  props: {
    filterList: {
      type: Array
    }
  }, 
  data() {
    return {
      value: '',
      useKeyboardEvent: true
    }
  },
  methods: {
    emitUpdateHandler(todo) {
      this.$emit('updateTaskHandler', todo);
    },
    emitDeleteHandler(index) {
      this.$emit('deleteTaskHandler', index);
    },
    emitEditHandler(index, newTaskContent) {
      this.$emit('editTaskHandler', index, newTaskContent);
      this.useKeyboardEvent = !this.useKeyboardEvent;
    } 
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