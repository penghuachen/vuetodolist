<template>
  <div class="content">
    <task-status></task-status>
    <task-content :todo-list="todoList"></task-content>
  </div>
</template>

<script>
import taskStatus from '@/components/task-status.vue';
import taskContent from '@/components/task-content.vue';

export default {
  props: {
    todoList: {
      type: Array
    }
  },
  components: {
    'task-status': taskStatus,
    'task-content': taskContent
  } 
}
</script>

<style lang="scss" scoped>
.content {
  position: relative;
  padding-top: 55px;
}
</style>