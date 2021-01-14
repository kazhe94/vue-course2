<template>
  <div class="card card-w70">
    <h3 v-if="personInfo.length ===0">Добавьте первый блок, чтобы увидеть результат</h3>
      <div v-else v-for="info in personInfo">
        <component
            :is="'person-' + info.optionType"
            :text="info.text"
            :key="info.id"
          >
          <delete-btn
              :id="info.id"
              @remove-block="removeBlock"
          >
          </delete-btn>
        </component>
      </div>
  </div>
</template>

<script>
import PersonAvatar from "./PersonInfo/PersonAvatar";
import PersonTitle from "./PersonInfo/PersonTitle";
import PersonText from "./PersonInfo/PersonText";
import PersonSubtitle from "./PersonInfo/PersonSubtitle";
import DeleteBtn from "./DeleteBtn";
export default {
  props: {
    personInfo: Object
  },
  name: "AppPersonInfo",
  components: {
    PersonAvatar,
    PersonTitle,
    PersonText,
    PersonSubtitle,
    DeleteBtn
  },
  methods: {
    removeBlock(id) {
      this.$emit('remove-block', id)
    }
  }
}
</script>

<style scoped>

</style>