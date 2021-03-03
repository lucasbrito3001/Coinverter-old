<template>
    <button type="button" class="btn-primary" v-on:click="changeCurrency">{{moeda}} para BRL</button>   
</template>

<script>
export default {
    props: ["moeda"],
    
    methods: {
        changeCurrency(){
            this.$emit('change')
        }
    }
}
</script>

<style scoped>
button{
    outline: none;
    border: none;
}

.btn-primary{
    border: none;
    margin: 10px;
    padding: 1px 4px;
    border-radius: 5px;
}
</style>