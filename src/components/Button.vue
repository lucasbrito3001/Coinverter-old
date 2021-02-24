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
.btn-primary{
    border: none;
    margin: 10px;
    border-radius: 5px;
}
</style>