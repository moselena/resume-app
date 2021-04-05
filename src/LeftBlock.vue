<template>
    <form class="card card-w30" @submit.prevent="submitHandler">
      <div class="form-control">
        <label for="type">Тип блока</label>
        <select id="type" v-model="type">
          <option value="title">Заголовок</option>
          <option value="subtitle">Подзаголовок</option>
          <option value="avatar">Аватар</option>
          <option value="text">Текст</option>
        </select>
      </div>

      <div class="form-control">
        <label for="value">Введите текст/ссылку на фото</label>
        <textarea id="value" rows="3" v-model="text"></textarea>
      </div>

      <MyButton
        :class="{ primary: !this.isDisabled }"
        :disabled="this.isDisabled"
        @click="$emit('addData', {text, type})">
          Добавить
      </MyButton>
    </form>
</template>
<script>

import MyButton from "./MyButton"
export default {
  emits: ["addData"],
  data() {
    return {
      text: '',
      type: 'title'
    }
  },
  methods: {
    submitHandler() {
      this.text = ''
    }
  },
  computed: {
    isDisabled() {
      return this.text.length <= 3;
    }
  },
  components: {MyButton}
}
</script>
<style>
    
</style>