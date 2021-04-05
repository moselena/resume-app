<template>
  <div class="container">
    <Loader v-if="loading" />
    <div v-else>
      <div class="card" v-if="comments.length" >
        <h2>Комментарии</h2>
        <ul class="list">
          <li class="list-item"
            v-for="comment in comments"
            :key="comment.id">
            <div>
              <p><strong>{{comment.email}}</strong></p>
              <small>{{comment.body}}</small>
            </div>
          </li>
        </ul>
      </div>
      <p v-else>
        <MyButton class="primary" @click="load">Загрузить комментарии</MyButton>
      </p>
    </div>
  </div>
</template>

<script>
import MyButton from "./MyButton"
import Loader from "./Loader"
export default {
    data() {
      return { 
        comments: [],
        loading: false
      }
    },
    methods: {
      async load() {
        this.loading = true
        try {
          const res = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42')
          this.comments = await res.json()
          this.loading = false
        } catch {
          console.log("fail")
        }
      }
    },
    components: {MyButton, Loader}
}
</script>

<style>
    
</style>

// https://resume-app-f5362-default-rtdb.firebaseio.com/