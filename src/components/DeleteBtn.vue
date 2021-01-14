<template>
  <button class="btn danger" @click="removeBlock">Удалить</button>
</template>

<script>
export default {
  name: "DeleteBtn",
  emits: ['remove-block'],
  props: {
    id: String
  },
  methods: {
    removeBlock() {
      this.$emit('remove-block', this.id)
    }
  }
}
</script>

<style scoped>

</style>