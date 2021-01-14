<template>
  <div class="person__block">
    <div class="avatar">
      <img :src="text" alt="avatar">
    </div>
    <slot></slot>
  </div>
</template>

<script>
import DeleteBtn from "../DeleteBtn";

export default {
  props: {
    text: String
  },
  components: {
    DeleteBtn
  },
  name: "PersonAvatar"
}

</script>

<style scoped>
  .avatar {
    margin-left: auto;
    margin-right: auto;
  }
</style>