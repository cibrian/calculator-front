<template>
  <div>
    <div class="container mx-auto p-3" style="width: 600px;">
      <select class="form-select mt-3" v-model="selectedOption">
          <option value=''>Open this select menu</option>
          <option value="addition">Addition</option>
      </select>
    </div>
    <Addition v-if="selectedOption == 'addition'"/>
  </div>
</template>

<script>
  import Addition from '@/components/Addition.vue'
  
  export default {
    name: "DashboardView",
    components:{
      Addition,
    },
    data(){
      return{
        selectedOption: ''
      }
    }
  }
</script>