<template>
  <div class="home container">
    <div>
    <b-form @submit.prevent="login">
      <b-form-group
        id="input-group-1"
        label="Email address:"
        label-for="input-1"
      >
        <b-form-input
          type="email"
          v-model="email"
          placeholder="Enter email"
          required
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Your Name:" label-for="input-2">
        <b-form-input
          type="password"
          v-model="password"
          placeholder="Enter password"
          required
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
    </b-form>
    
  </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HomeView',
  components: {
  },
  data(){
    return{
      email:"",
      password:""
    }
  },
  methods:{
    login(){
      let credentials = {
        "email": this.email,
        "password": this.password
      };
      axios.post('http://127.0.0.1/api/v1/login', credentials)
      .then(data=>{
        localStorage.token = data.data.token;
        this.$router.push('dashboard');
      });
    }
  }
}
</script>
