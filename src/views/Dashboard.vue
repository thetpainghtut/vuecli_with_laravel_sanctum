<template>
  <div class="dashboard">
    <h1>This is an dashboard page</h1>
    <p><strong>Auth Username: </strong> {{user.name}}</p>

    <button @click="logout">Logout</button>
  </div>
</template>

<script type="text/javascript">
  import axios from 'axios'

  axios.defaults.withCredentials = true;
  axios.defaults.baseURL = 'http://localhost:8000';

  export default{
    data(){
      return{
        user: Object
      }
    },
    mounted(){
      axios.get('/api/user').then(response => {
        console.log(response)
        this.user = response.data
      });
    },
    methods:{
      logout(){
        axios.post('logout').then(response => {
          this.$router.push({name: 'Home'})
        })
      }
    }
  }
</script>