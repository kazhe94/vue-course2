<template>
  <div class="container column">
    <app-form
        @submit-form="saveInfo"
    ></app-form>

    <app-person-info
      :person-info="personInfo"
      @remove-block="removeBlock"
    ></app-person-info>
  </div>
  <div class="container">
    <app-comments
        :comments="comments"
        :loading="loading"
        @load-comments="loadComments"
    ></app-comments>

  </div>
</template>

<script>
import AppComments from "./components/comments/AppComments";
import AppForm from "./components/AppForm";
import AppPersonInfo from "./components/AppPersonInfo";

export default {
  components: {
    AppComments,
    AppForm,
    AppPersonInfo,
  },
  data() {
    return {
      loading: false,
      comments: [],
      personInfo: []
    }
  },
  async mounted() {
    const response = await fetch('https://vue-course2-305f0-default-rtdb.europe-west1.firebasedatabase.app/info.json', {
      method: 'GET',
      headers: {
        'Content-Type': 'application/json'
      },
    })
    const data = await response.json()
    if(data) {
      this.personInfo = Object.keys(data).map(key=> {
        return {
          id: key,
          ...data[key]
        }
      })
    } else {
      this.personInfo = []
    }


  },
  methods: {
    async loadComments() {
      this.loading = true
      const response = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=10')
      this.comments = await response.json()
      this.loading = false
    },
    async saveInfo(newText) {
      const response = await fetch('https://vue-course2-305f0-default-rtdb.europe-west1.firebasedatabase.app/info.json', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(newText)
      })
      const data = response.json()
      console.log()
      this.personInfo.push({
        id: data.name,
        optionType: newText.optionType,
        text: newText.text
      })
    },
    async removeBlock(id) {
      await fetch(`https://vue-course2-305f0-default-rtdb.europe-west1.firebasedatabase.app/info/${id}.json`, {
        method: 'delete'
      })
      this.personInfo = this.personInfo.filter(item=> item.id !== id)
    }
  }
}
</script>

<style>
  .avatar {
    display: flex;
    justify-content: center;
  }

  .avatar img {
    width: 150px;
    height: auto;
    border-radius: 50%;
  }
  .person__block {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
</style>
