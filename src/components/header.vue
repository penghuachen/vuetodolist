<template>
  <div class="header">
    <refreshIcon 
      class="refresh"
      @click="deleteAllTasks"
      />
    <p class="date">{{ currentDate }}</p>
  </div>
</template>

<script>
import moment from 'moment' 

import refreshIcon from '@/assets/img/refresh-icon.svg'

export default {
  props: {
    todoList: {
      type: Array
    }
  },
  methods: {
    deleteAllTasks() {
      let deleteCheck = confirm('您確定要刪除全部任務嗎?');
      if(deleteCheck) {
        alert('刪除全部任務。')
        return this.$emit('update:todoList', []);
      }
      alert('取消刪除。')
    }
  },
  computed: {
    currentDate() {
      return moment().format('dddd, MMM D'); 
    }
  },
  components: {
    refreshIcon
  }
}
</script>

<style lang="scss" scope>
.header {
  height: 200px;
  border-radius: 15px 15px 0 0;
  background: url('~@/assets/img/bg.jpg') no-repeat 50% 70%;
  background-size: cover;
  position: relative;
  .refresh {
    position: absolute;
    width: 28px;
    height: 28px;
    right: 20px;
    top: 20px;
    transition: all .2s;
    color: rgba(255, 255, 255, 1);
    &:hover {
      transform: rotate(40deg);
    }
  }
  .date {
    position: absolute;
    left: 10px;
    bottom: 10px;
    font-size: 25px;
    color: rgba(255, 255, 255, 1);
    font-weight: bold;
  }
}
</style>