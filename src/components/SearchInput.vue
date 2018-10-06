<template>
    <div class="searchWrapper">
        <input 
          id="search" 
          name="search" 
          v-model="searchValue"
          @input="handleInput"
        />
    </div>
</template>

<script>
export default {
    name: 'SearchInput',
}
</script>

<style lang="scss" scoped> 
    .searchWrapper{
        display: flex;
        flex-direction: column;
        width: 95%;
        margin-top: 50px;
        max-width: 300px;

        input{
        height: 30px;
        border: 0;
        background: none;
        border-bottom: 1px solid black;
        outline: none;
        }
  }
</style>
