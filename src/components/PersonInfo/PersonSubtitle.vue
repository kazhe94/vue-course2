<template>
  <div class="person__block">
    <h2>{{ text }}</h2>
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
  name: "PersonSubtitle"
}
</script>

<style scoped>

</style>