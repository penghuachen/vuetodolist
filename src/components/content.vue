<template>
  <div class="content">
    <task-status 
      :statusArea="statusArea"
      @updateStatusAreaHandler="emitUpdateAreaHandler"
      />
    <task-content 
      :filter-list="filterList"
      @updateTaskHandler="emitUpdateHandler"
      @deleteTaskHandler="emitDeleteHandler"
      @editTaskHandler="emitEditHandler"
    />
  </div>
</template>

<script>
import taskStatus from '@/components/task-status.vue';
import taskContent from '@/components/task-content.vue';

export default {
  props: {
    filterList: {
      type: Array
    },
    statusArea: {
      type: String
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
    },
    emitUpdateAreaHandler(area) {
      this.$emit('updateStatusAreaHandler', area)
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