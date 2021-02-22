<template>
  <div class="block-container" :class="{ 'discovered': value === 100 }" @click="$emit('discover')">
    <h4 class="block-value">
      {{ value }}
    </h4>
  </div>
</template>

<script>
export default {
  name: 'CountBlock',

  props: {
    value: {
      type: Number,
      default: 0
    }
  }
}
</script>

<style scoped lang="scss">
.block-container {
  display: flex;
  justify-content: center;
  align-content: center;

  width: 200px;
  height: 200px;

  margin: 20px auto;
  border: 1px solid gray;
  background-color: #dedede;

  &.discovered {
    border-color: #c80dc8;
    background-color: #e29fe2;
  }

  .block-value {
    margin: auto;
  }
}
</style>
