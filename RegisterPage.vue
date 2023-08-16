<template>
    <div class="container">
        <h1>Register</h1>
        <form  @submit.prevent="handleSubmit">
        <div class="form-group">
            <label>First name</label>
            <input type="text" class="form-control" v-model="first_name" placeholder="First name">
        </div>
        <div class="form-group">
            <label>Last name</label>
            <input type="text" class="form-control" v-model="last_name"  placeholder="Last name">
        </div>
        <div class="form-group">
            <label>Email</label>
            <input type="email" class="form-control" v-model="email" placeholder="Email">
        </div>
        <div class="form-group">
            <label>Password</label>
            <input type="password" class="form-control" v-model="password" placeholder="Password">
        </div>
        <div class="form-group">
            <label>Comfirm Password</label>
            <input type="password" class="form-control" v-model="password_confirm" placeholder="Comfirm Password">
        </div>
        <button class="btn btn-primary btn-block">Register</button>
    </form>
    </div>
      
  </template>
  
  <script> 
  import axios from 'axios'
  export default {
    name: 'RegisterPage',

    data(){

        return{

            first_name: '',
            last_name: '',
            email: '',
            password:'',
            password_confirm: ''

                }

    },

    methods: {
      async  handleSubmit(){ 
            
        const response = await axios.post('register', {
                first_name: this.first_name,
                last_name: this.last_name,
                email: this.email,
                password: this.password,
                password_confirm: this.password_confirm
            });

            console.log(response);
            this.$route.push('/login');
        }
    
    }
  }
  </script>