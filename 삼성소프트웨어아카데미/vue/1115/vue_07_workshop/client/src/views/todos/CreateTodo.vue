<template>
  <div>
    <input 
      type="text" 
      v-model.trim="title" 
      @keyup.enter="createTodo"
    >
    <button @click="createTodo">+</button>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'CreateTodo',
  data: function () {
    return {
      title: null,
    }
  },
  methods: {
    createTodo: function () {
      axios({
        method: 'post',
        url: 'http://127.0.0.1:8000/todos/',
        data: {
          title: this.title
        }
      })
        .then(() => {
          //console.log(res)
          this.$router.push({ name: 'TodoList'})
        })
        .catch(err => {
          console.log(err)
        })
    }
  }
}
</script>
