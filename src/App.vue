<template>
  <div class="app">
    <div class="wrapper">
      <Background />
      <Claim />
      <SearchInput 
        v-model="searchValue"
        @input="handleInput"
      />
    </div>
  </div>
</template>

<script>
  import axios from 'axios';
  import debounce from 'lodash.debounce';
  import Claim from '@/components/Claim.vue';
  import SearchInput from '@/components/SearchInput.vue';
  import Background from '@/components/Background.vue';

  const API = 'https://images-api.nasa.gov/search';

  export default {
    name: 'App',
    components: {
      Claim,
      SearchInput,
      Background,
    },
    data(){
      return{
        searchValue: '',
        results: [],
      };
    },
    methods: {
      handleInput: debounce(function(){
        console.log(this.searchValue);
        axios.get(`${API}?q=${this.searchValue}&media_type=image`)
          .then((response) => {
            this.results = response.data.collection.items;
          })
          .catch((error) => {
            console.log(error);
          });
      }, 500),
    },
  };
</script>

<style lang="scss" scoped>
  @import url('https://fonts.googleapis.com/css?family=Montserrat:100,100i,200,200i,300,300i,400,400i,500,500i,600,600i,700,700i,800,800i,900,900i');
  @import url('https://meyerweb.com/eric/tools/css/reset/reset.css');

  * {
    box-sizing: border-box;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }
  body{
    font-family: Montserrat, sans-serif;
    margin: 0;
    padding: 0;
  }
  .wrapper{
    display: flex;
    flex-direction: column;
    align-items: center;
    box-sizing: border-box;
    padding: 30px;
    margin: 0;
    width: 100%;
    min-height: 100vh;
    font-family: Montserrat, sans-serif;
    text-align: center;
    justify-content: center;
    align-items: center;
  }
</style>
