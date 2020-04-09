<template>
  <div class="task-status">
    <p class="all-task"
      :class="{ current : statusArea == '全部' }"
      @click="emitUpdateAreaHandler($event)"
      >
      全部
    </p>
    <p class="doing-task"
      :class="{ current : statusArea == '進行中' }"
      @click="emitUpdateAreaHandler($event)"
    >
      進行中
    </p>
    <p class="finished-task"
      :class="{ current : statusArea == '已完成' }"
      @click="emitUpdateAreaHandler($event)"
      >
      已完成
    </p>
  </div>
</template>

<script>
export default {
  props: {
    statusArea: {
      type: String
    }
  },
  methods: {
    emitUpdateAreaHandler(event) {
      let currentArea = event.target.textContent.trim();
      this.$emit('updateStatusAreaHandler', currentArea);
    }
  },
}
</script>

<style lang="scss" scoped>
  .task-status {
    position: absolute;
    display: flex;
    top: 0;
    left: 0;
    right: 0;
    border-bottom: 1px solid #8d8d88;
    box-shadow: 0px 3px 5px #9d9d9d;
    > p {
      flex: 0 1 33.33%;
      text-align: center;
      height: 55px;
      line-height: 55px;
      letter-spacing: 3px;
      font-size: 20px;
      cursor: pointer;
    }
    .current {
      background: #F17;
      color: #fff;
    }
  }

</style>