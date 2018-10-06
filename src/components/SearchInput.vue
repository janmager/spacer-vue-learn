<template>
    <input 
        id="search" 
        name="search"
        :value="value"
        @input="handleChange"
    />
</template>

<script>
export default {
    name: 'SearchInput',
    props: {
        value: {
            type: String,
            required: true,
        }
    },
    methods: {
        handleChange(e){
            this.$emit('input', e.target.value);
        },
    },
}
</script>

<style lang="scss" scoped> 
    input{
            margin-top: 50px;
            display: flex;
            color: white;
            text-align: center;
            font-size: 18px;
            font-family: Montserrat, sans-serif;    
            height: 30px;
            border: 0;
            background: none;
            border-bottom: 2px solid white;
            transition: box-shadow ease-out .3s;

            @media (min-width: 1024px){
                font-weight: 400px;
            }
    }

    input:focus{
        outline: none;
        box-shadow: 0 10px 20px -8px rgba(255,255,255,0.6);
    }
</style>
