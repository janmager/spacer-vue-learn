<template>
  <div class="home">
    <div class="wrapper">
      <Claim />
      <div class="search">
        <label for="search">Search</label>
        <input 
          id="search" 
          name="search" 
          v-model="searchValue"
          @input="handleInput"
        />
      </div>
    </div>
  </div>
</template>

<script>
  import axios from 'axios';
  import debounce from 'lodash.debounce';
  import Claim from '@/components/Claim.vue';

  const API = 'https://images-api.nasa.gov/search';

  export default {
    name: 'Search',
    components: {
      Claim,
    },
    data(){
      return{
        searchValue: '',
        results: [],
      };
    },
    methods: {
      handleInput: debounce(function(){
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
  .wrapper{
    display: flex;
    flex-direction: column;
    align-items: center;
    box-sizing: border-box;
    padding: 30px;
    margin: 0;
    width: 100%;
  }

  .search{
    display: none;
    flex-direction: column;
    width: 95%;
    max-width: 300px;

    label{
      font-family: Montserrat, sans-serif;
    }

    input{
      height: 30px;
      border: 0;
      border-bottom: 1px solid black;
      outline: none;
    }
  }
</style>