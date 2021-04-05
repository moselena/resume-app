<template>
  <div class="container">
    <div class="card card-w100">
      <h2>Генератор резюме</h2>
    </div>
    <div class="container column">
      <LeftBlock 
        @add-data="onAddData" />
      <RightBlock 
        :blocks="blocks" />
    </div>
    <Comments />
  </div>
</template>

<script>
import LeftBlock from './LeftBlock.vue'
import RightBlock from './RightBlock.vue'
import Comments from "./Comments.vue"
export default {
  data() {
    return {
      blocks: []
    }
  },
  methods: {
    onAddData(block) {
      this.blocks.push(block);
    }
  },
  components: {
    LeftBlock: LeftBlock,
    RightBlock: RightBlock,
    Comments: Comments
  }
}
</script>
    

<style>
  .avatar {
    display: flex;
    justify-content: center;
  }

  .avatar img {
    width: 150px;
    height: auto;
    border-radius: 50%;
  }
</style>