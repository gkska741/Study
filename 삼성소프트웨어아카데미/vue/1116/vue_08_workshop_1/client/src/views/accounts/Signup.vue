<template>
  <div>
    <h1>Signup</h1>
    <div>
      <label for="username"> 사용자 이름: </label>
      <input 
        type="text"
        id="username"
        v-model="credentials.username"
      >
    </div>

    <div>
      <label for="password"> 비밀번호: </label>
      <input 
        type="password"
        id="password"
        v-model="credentials.password"
      >
    </div>

    <div>
      <label for="passwordConfirmation"> 비밀번호 확인: </label>
      <input 
        type="password"
        id="passwordConfirmation"
        v-model="credentials.passwordConfirmation"
        @keyup.enter="signup"
      >
      <button @click="signup"> 회원가입 </button>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

// const SERVER_URL = process.env.VUE_APP_SERVER_URL

export default {
  name: 'Singup',
  data: function () {
    return {
      credentials: {
        username: null,
        password: null,
        passwordConfirmation: null,
      },
    }
  },
  methods: {
    signup: function () {
      axios({
        method: 'post',
        url: 'http://127.0.0.1:8000/accounts/signup/',
        data: this.credentials
      })
        .then( (res) => {
          console.log(res)

          localStorage.setItem('jwt', res.data.token)
          this.$emit('Login')
          this.$router.push({ name: 'Login' })
          
        })
        .catch(err => {
          console.log(err)
        })
    }
  }
}
</script>