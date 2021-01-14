<template>
  <div class="person__block">
    <p>
      {{text}}
    </p>
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
  name: "PersonText"
}
</script>

<style scoped>

</style>