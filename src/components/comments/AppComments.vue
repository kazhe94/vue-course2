<template>
  <p>
    <button
        class="btn primary"
        @click="loadComments"
        v-if="comments.length === 0"
    >Загрузить комментарии</button>
  </p>
  <div class="card" v-if="comments.length !==0">
    <h2>Комментарии</h2>
    <ul class="list">
        <app-comment-item
            v-for="comment in comments"
            :comment="comment"
            :key="comment.id"
        ></app-comment-item>
    </ul>
  </div>
  <app-loader v-if="loading"></app-loader>
</template>

<script>
import AppCommentItem from "./AppCommentItem";
import AppLoader from "../AppLoader";
export default {
  props: {
    comments: Array,
    loading: Boolean
  },
  name: 'AppComments',
  emits: ['load-comments'],
  components: {
    AppCommentItem,
    AppLoader
  },
  methods: {
    loadComments() {
      this.$emit('load-comments')
    }
  }
}
</script>

<style scoped>

</style>