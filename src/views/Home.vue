<template>
  <div class="home">
    <h1>Login Page</h1>
    <form @submit.prevent="login">
      <div>
        <input type="email" name="email" placeholder="Email...">
      </div>
      <div>
        <input type="password" name="password" placeholder="Password...">
      </div>
      <div>
        <input type="submit" name="btnsubmit" value="Login">
      </div>
    </form>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'

axios.defaults.withCredentials = true;
axios.defaults.baseURL = 'http://localhost:8000';

export default {
  name: 'Home',
  methods:{
    login(){
      axios.get('/sanctum/csrf-cookie').then(response => {
        axios.post('/login',{
          email: 'user@user.com',
          password: 'password'
        })
        .then(response=>{
          // console.log(response)
          this.$router.push({name: 'Dashboard'})
        })
      });
    }
  }
}
</script>
