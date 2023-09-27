<template>
  <div class="text-center container justify-content-center d-grid mt-5 pt-5">
    <h3 class="text-secondary h3 mt-2">Autocomplete Vue.js</h3>
    <Autocomplete :items="names"></Autocomplete>
  </div>
</template>
<script>
  import Autocomplete from './components/Autocomplete.vue';

  export default {
    name: 'App',
    components: {
    Autocomplete
},
    data() {
      return {
        names: ''
      }
    },
    methods: {
      async getNames(){
        const request = await fetch('http://localhost:3000/data')
        const result = await request.json()
        
        if(request.status === 200){
          this.names = result
        }
      }
    },

    created(){
      this.getNames()
    }
  }

</script>
<style scoped>
</style>

