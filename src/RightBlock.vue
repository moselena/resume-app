<template>
    <div class="card card-w70">
      <p v-if="blocks.length === 0">Добавьте первый блок, чтобы увидеть результат</p>
      <div v-for="(block, index) in blocks" :key="index">
        <component :is="block.type" :block="block"></component>
      </div>
    </div>
</template>
<script>
import Title from './Title.vue'
import Avatar from './Avatar.vue'
import Subtitle from './Subtitle.vue'
import Text from './Text.vue'
export default {
  data() {
    return {
    }
  },
  components: {
    'title': Title,
    'avatar': Avatar,
    'subtitle': Subtitle,
    'text': Text
  },
  props: ['blocks']
}
</script>
<style>
    
</style>