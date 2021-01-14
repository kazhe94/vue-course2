<template>
  <li class="list-item">
    <div>
      <p><strong>{{ comment.email }}</strong></p>
      <small>{{ comment.name }}</small>
    </div>
  </li>
</template>

<script>
export default {
  props: {
    comment: Object
  },
  name: 'AppCommentItem'
}
</script>

<style scoped>

</style>