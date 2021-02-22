<template>
  <b-container class="p-sm2 p-lg-5">
    <b-row>
      <b-col class="text-left">
        <h2>
          {{ initData.title }}
        </h2>
        <p>
          {{ initData.description }}
        </p>
      </b-col>

      <b-col>
        <div class="block-wrapper">
          <CountBlock :value="blockItem.value" v-for="(blockItem, index) in initData.blocks" :key="blockItem.id" @discover="discover(index)"></CountBlock>
        </div>
      </b-col>
    </b-row>

    <b-modal id="end-modal">Good job on completing your collection!</b-modal>
  </b-container>
</template>

<script>
// @ is an alias to /src
import CountBlock from '@/components/CountBlock'
import mock from '../fixtures/mock.json'

export default {
  name: 'Home',
  components: {
    CountBlock
  },

  data() {
    return {
      initData: mock
    }
  },

  methods: {
    discover(itemIndex) {
      const discoveredCount = this.initData.blocks.filter(item => item.value === 100).length;
      if (discoveredCount === this.initData.blocks.length) {
        // if already completed, do nothing
        return;
      }

      if (this.initData.blocks[itemIndex].value < 100) {
        this.initData.blocks[itemIndex].value = 100;
      }

      // if all completed, show modal
      if (discoveredCount === this.initData.blocks.length - 1) {
        this.$bvModal.show('end-modal');
      }
    }
  }
}
</script>

<style scoped lang="scss">
.block-wrapper {
  display: flex;
  justify-content: space-around;
  align-content: center;
  flex-wrap: wrap;
}
</style>
