<template>
  <div class="home">
    <div class="wrapper">
      <Claim />
      <SearchInput />
    </div>
  </div>
</template>

<script>
  import axios from 'axios';
  import debounce from 'lodash.debounce';
  import Claim from '@/components/Claim.vue';
  import SearchInput from '@/components/SearchInput.vue';

  const API = 'https://images-api.nasa.gov/search';

  export default {
    name: 'Search',
    components: {
      Claim,
      SearchInput,
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
    min-height: 100vh;
    font-family: Montserrat, sans-serif;
    text-align: center;
    justify-content: center;
    align-items: center;
    background-image: url('../assets/bg.jpg');
    background-repeat: no-repeat;
    background-size: cover;
    background-position: 50% 0%;
  }
</style>