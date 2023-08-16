<template>
    <div class="container">
        <h1>Login</h1>
        <form @submit.prevent="">
        <div class="form-group">
            <label>Email</label>
            <input type="email" class="form-control" v-model="email"  placeholder="Email">
        </div>
        <div class="form-group">
            <label>Password</label>
            <input type="password" class="form-control" v-model="password"  placeholder="Password">
        </div>
        <button class="btn btn-primary btn-block">Login</button>
    </form>
    </div>
      
  </template>
  
  <script>
  import axios from 'axios'
  export default {
    name: 'LoginPage',
    data(){

        return{

            email: '',
            password:''

                }

        },

        methods: {
            async  handleSubmit(){ 
                    
                const response = await axios.post('login', { 
                        email: this.email,
                        password: this.password

                    });

                    localStorage.setItem('token', response.data.token);
                    this.$route.push('/home');
                }
    
         }
  }
  </script>