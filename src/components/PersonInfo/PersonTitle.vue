<template>
  <div class="person__block">
    <h1>{{ text }}</h1>
    <slot></slot>
  </div>
</template>

<script>
import DeleteBtn from "../DeleteBtn";

export default {
  props:  {
    text: String
  },
  components: {
    DeleteBtn
  },
  name: "PersonTitle"
}
</script>

<style scoped>

</style>
