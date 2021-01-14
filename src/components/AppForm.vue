<template>
  <form @submit.prevent="submitForm" class="card card-w30">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="selectOption">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea id="value" rows="3" v-model.trim="inputText"></textarea>
    </div>

    <button :disabled="!isActive" class="btn primary">Добавить</button>
  </form>
</template>

<script>
export default {
  name: "AppForm",
  emits: ['submit-form'],
  data() {
    return {
      selectOption: 'title',
      inputText: '',
    }
  },
  computed: {
    isActive() {
      return this.inputText.length > 3
    }
  },
  methods: {
    isValid() {
      if(this.inputText.length < 3) {
        return false
      }
      return true;
    },
    submitForm() {
      if(this.isValid()) {
        this.$emit('submit-form', {
          optionType: this.selectOption,
          text: this.inputText
        })
        this.inputText = ''
        this.selectOption = 'title'
      }
    }
  }
}
</script>

<style scoped>

</style>