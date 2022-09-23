<template>
  <div>
    <div class="container mx-auto p-3" style="width: 600px;">
     <form @submit.prevent="addition">
      <div class="row">
        <div class="col-3">
          <input type="number" class="form-control" v-model.number="value1">
        </div>
        <div class="col-3">
          <input type="number" class="form-control" v-model.number="value2">
        </div>
        <div class="col-3">
          <input type="number" class="form-control" v-model.number="result" readonly>
        </div>
        <div class="col-3">
          <button type="submit" class="btn btn-primary">Calculate</button>
        </div>
      </div>
    </form>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'AdditionComponent',
  data(){
    return{
      value1: 0,
      value2: 0,
      result: 0
    }
  },
  methods:{
    addition(){
      let params = {
        "type": "addition",
        "value1": this.value1,
        "value2": this.value2
      };
      const token = localStorage.getItem("token");
      axios.post(
       'http://127.0.0.1/api/v1/calculator', 
        params,
        {
          headers: {
            'Authorization': `Bearer ${token}`
          },
        }
      )
      .then(data=>{
        this.result = data.data.result;
      });
    }
  }
}
</script>

