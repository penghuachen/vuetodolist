<template>
  <div class="task-status">
    <p class="all-task current">全部</p>
    <p class="doing-task">進行中</p>
    <p class="finished-task">已完成</p>
  </div>
</template>

<script>
export default {
  
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